<template>
    <div class="tasks-view">
      <div class="close-button">
        <span class="close-icon">×</span>
      </div>
      
      <tasks-header 
        :activeTab="activeTab" 
        @update-tab="updateActiveTab" 
      />
      
      <div class="tasks-content">
        <tasks-section 
          v-if="activeTab === 'daily' || activeTab === 'tasks'"
          title="Onboarding" 
          :tasks="onboardingTasks" 
          @start-task="startTask" 
          @claim-reward="claimReward" 
        />
        
        <tasks-section 
          v-if="activeTab === 'daily' || activeTab === 'tasks'"
          title="In game" 
          :tasks="inGameTasks" 
          @start-task="startTask" 
          @claim-reward="claimReward" 
        />
        
        <tasks-section 
          v-if="activeTab === 'special'"
          title="Special Events" 
          :tasks="specialTasks" 
          @start-task="startTask" 
          @claim-reward="claimReward" 
        />
      </div>
    </div>
  </template>
  
  <script>
  import TasksHeader from '../components/TasksHeader.vue';
  import TasksSection from '../components/TasksSection.vue';
  
  export default {
    name: 'TasksView',
    components: {
      TasksHeader,
      TasksSection
    },
    data() {
      return {
        activeTab: 'daily',
        onboardingTasks: [
          { id: 1, name: 'Follow us on X', reward: 100, status: 'completed' },
          { id: 2, name: 'Follow us on X', reward: 100, status: 'pending' },
          { id: 3, name: 'Follow us on X', reward: 100, status: 'pending' },
          { id: 4, name: 'Follow us on X', reward: 100, status: 'pending' },
          { id: 5, name: 'Follow us on X', reward: 100, status: 'pending' }
        ],
        inGameTasks: [
          { id: 6, name: 'Follow us on X', reward: 100, status: 'pending' },
          { id: 7, name: 'Follow us on X', reward: 100, status: 'pending' }
        ],
        specialTasks: [
          { id: 8, name: 'Special weekend event', reward: 200, status: 'pending' },
          { id: 9, name: 'Join our Discord', reward: 150, status: 'pending' }
        ]
      }
    },
    methods: {
      updateActiveTab(tabId) {
        this.activeTab = tabId;
      },
      startTask(taskId) {
        // Logic to start a task would go here
        console.log('Starting task:', taskId);
        
        // For demo purposes, let's update the task status
        const updateTaskStatus = (tasksArray) => {
          const taskIndex = tasksArray.findIndex(task => task.id === taskId);
          if (taskIndex !== -1) {
            tasksArray[taskIndex].status = 'completed';
          }
        };
        
        updateTaskStatus(this.onboardingTasks);
        updateTaskStatus(this.inGameTasks);
        updateTaskStatus(this.specialTasks);
      },
      claimReward(taskId) {
        // Logic to claim a reward would go here
        console.log('Claiming reward for task:', taskId);
        
        // For demo purposes, let's mark the task as claimed by removing it
        const removeTask = (tasksArray) => {
          const taskIndex = tasksArray.findIndex(task => task.id === taskId);
          if (taskIndex !== -1) {
            tasksArray.splice(taskIndex, 1);
          }
        };
        
        removeTask(this.onboardingTasks);
        removeTask(this.inGameTasks);
        removeTask(this.specialTasks);
      }
    }
  }
  </script>
  
  <style scoped>
  .tasks-view {
    min-height: 100vh;
    background-image: linear-gradient(rgba(255, 136, 0, 0.6), rgba(255, 136, 0, 0.6)), url('../assets/images/background.jpg');
    background-size: cover;
    background-position: center;
    padding: 20px;
    position: relative;
  }
  
  .close-button {
    position: absolute;
    top: 20px;
    right: 20px;
    width: 40px;
    height: 40px;
    background-color: #132446;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 8px;
    cursor: pointer;
  }
  
  .close-icon {
    color: #FFD700;
    font-size: 28px;
    font-weight: bold;
  }
  
  .tasks-content {
    margin-top: 20px;
  }
  </style>
  