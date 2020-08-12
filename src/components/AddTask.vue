<template>
  <div class="form">
    <form @submit.prevent="addTask">
      <fieldset>
        <div>
          <input type="text" v-model="item" placeholder="E.g. Go Home...">
          <Button>등록하기</Button>
        </div>
      </fieldset>
    </form>
  </div>
</template>

<script>
import Button from './atoms/Button';
// import Input from './atoms/Input';

export default {
  components: {
    Button,
    // Input
  },

  data() {
    return {
      item: [],
    }
  },

  methods: { 
    addTask() {
      const item = this.item;
      const id = new Date().getTime();
      const isEmpty = item.length <= 0
      
      if (isEmpty) return false; 

      this.$emit('addTask', { id, item });
      this.resetInput();
    },

    resetInput() {
      this.item = '';
    }
  }
}
</script>

<style lang="scss" scoped>

</style>