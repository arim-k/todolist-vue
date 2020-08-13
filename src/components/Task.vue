<template>
  <li class="task">
    <div @dblclick="handleDblClick">
      <template v-if="!isChanging">
        <span>
          {{ task.item }}
        </span>
      </template> 
      <input 
        v-else
        type="text"
        ref="item"
        :value="task.item"
        @blur="handleBlur"
        @keydown.enter="updateTask"
      /> 
      <Button @click="updateTask">Update</Button>
      <Button @click="deleteTask">Delete</Button>
    </div>
  </li> 
</template>

<script>
import Button from './atoms/Button';

export default {
  components: {
    Button
  },

  props: {
    task: {
      type: Object
    }
  },

  data() {
    return {
      isChanging: false
    }
  },

  methods: {
    deleteTask() {
      const id = this.task.id;
      this.$emit('deleteTask', id);
    },

    handleDblClick() {
      this.isChanging = true;
      console.log('handleDblCllick =>', this.$refs.item);
      
      this.$nextTick(() => {
        this.isChanging = true;
        this.$nextTick(() => {
          this.$refs.item.focus();
        })
      })
    },

    updateTask(e) {
      const id = this.task.id;
      const item = e.target.value;
      console.log(id, item);
      
      if (item.length <= 0) {
        return false;
      }

      this.$emit('updateTask', { id, item });
      console.log(item)
      this.isChanging = false;
    },

    handleBlur() {
      this.isChanging = false;
    }
  }
}
</script>

<style lang="scss" scoped>

</style>