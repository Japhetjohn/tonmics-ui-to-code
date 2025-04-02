<template>
    <div class="tasks-section">
      <h3 class="section-title">{{ title }}</h3>
      <task-item 
        v-for="task in tasks" 
        :key="task.id" 
        :task="task" 
        @start-task="handleStartTask" 
        @claim-reward="handleClaimReward" 
      />
    </div>
  </template>
  
  <script>
  import TaskItem from './TaskItem.vue';
  
  export default {
    name: 'TasksSection',
    components: {
      TaskItem
    },
    props: {
      title: {
        type: String,
        required: true
      },
      tasks: {
        type: Array,
        required: true
      }
    },
    methods: {
      handleStartTask(taskId) {
        this.$emit('start-task', taskId);
      },
      handleClaimReward(taskId) {
        this.$emit('claim-reward', taskId);
      }
    }
  }
  </script>
  
  <style scoped>
  .tasks-section {
    margin-bottom: 30px;
  }
  
  .section-title {
    font-size: 24px;
    margin-bottom: 15px;
    color: white;
    font-weight: bold;
  }
  </style>
  