<template>
  <div id="app">
    <TaskListVue />
  </div>
</template>

<script>
import TaskListVue from './components/TaskList.vue'
export default {
  components: {
    TaskListVue
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 20px;
  display: flex;
}

h1 {
  font-size: 28px;
  margin-bottom: 20px;
}
</style>
