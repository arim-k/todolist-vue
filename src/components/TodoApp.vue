<template>
  <div class="todo-app">
    <AddTask @addTask="addTask" />
    <ul>
      <Task 
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @deleteTask="deleteTask"
      />
    </ul> 
  </div>
</template>

<script>
import AddTask from './AddTask';
import Task from './Task';

export default {
  components: {
    AddTask,
    Task
  },

  data() {
    return {
      tasks: [],
    }
  }, 

  methods: {
    addTask(data) {
      this.tasks.push(data);
      this.storeTask();
    },

    storeTask() {
      const tasksToString = JSON.stringify(this.tasks);
      localStorage.setItem('tasks', tasksToString)
    },

    deleteTask(id) {
      const targetIndex = this.tasks.findIndex(v => v.id === id);
      this.tasks.splice(targetIndex, 1);
      this.storeTask();
    }
  },

  created() {
    this.tasks = localStorage.tasks ? JSON.parse(localStorage.tasks) : [];
  }
}
</script>

<style lang="scss" scoped>

</style>