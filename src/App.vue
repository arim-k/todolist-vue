<template>
  <div id="app">
    <Header />
    <TodoApp />
  </div>
</template>

<script>
import Header from './components/Header';
import TodoApp from './components/TodoApp';

export default {
  name: 'App',  
  components: {
    Header,
    TodoApp
  }
}
</script>

<style>

</style>
