<template>
  <div>
    <li class="task">
      <span>{{ task.item }}</span>
      <Button>Update</Button>
      <Button @click="deleteTask">Delete</Button>
    </li>
  </div>  
</template>

<script>
import Button from './atoms/Button';

export default {
  props: {
    task: {
      type: Object
    }
  },

  methods: {
    deleteTask() {
      const id = this.task.id;
      this.$emit('deleteTask', id);
    }
  }
}
</script>

<style lang="scss" scoped>

</style>