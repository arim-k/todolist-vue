<template>
  <div class="todo-app">
    <AddTask @addTask="addTask" />
    <ul>
      <Task 
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @deleteTask="deleteTask"
        @updateTask="updateTask"
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
    },

    updateTask(data) { 
      const id = data.id;
      const item = data.item;
      const targetIndex = this.tasks.findIndex(v => v.id === id);
      const targetTask = this.tasks[targetIndex];
      console.log('targetTask', targetTask);
      this.tasks.splice(targetIndex, 1, { ...targetTask, item });

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