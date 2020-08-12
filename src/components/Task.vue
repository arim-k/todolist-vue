<template>
  <div>
    <li class="task">
      <span>{{ task.item }}</span>
      <Button>Delete</Button>
      <Button>Update</Button>
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
  }
}
</script>

<style lang="scss" scoped>

</style>