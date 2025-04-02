<template>
  <div id="app">
    <tasks-view />
  </div>
</template>

<script>
import TasksView from './views/TasksView.vue';

export default {
  name: 'App',
  components: {
    TasksView
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Arial', sans-serif;
  line-height: 1.6;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
