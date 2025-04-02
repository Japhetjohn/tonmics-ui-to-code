<template>
    <div class="task-item">
      <div class="task-content">
        <div class="task-icon">
          <div class="circle"></div>
        </div>
        <div class="task-description">
          <div class="task-name">{{ task.name }}</div>
          <div class="task-reward">
            <img src="../assets/images/coin.png" alt="Coin" class="coin-icon" />
            <span>+{{ task.reward }}</span>
          </div>
        </div>
      </div>
      <button 
        :class="['action-button', task.status === 'completed' ? 'claim-button' : 'start-button']" 
        @click="handleAction"
      >
        {{ task.status === 'completed' ? 'CLAIM' : 'START' }}
      </button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TaskItem',
    props: {
      task: {
        type: Object,
        required: true,
        default: () => ({
          name: '',
          reward: 0,
          status: 'pending' // 'pending', 'in-progress', 'completed'
        })
      }
    },
    methods: {
      handleAction() {
        if (this.task.status === 'completed') {
          this.$emit('claim-reward', this.task.id);
        } else {
          this.$emit('start-task', this.task.id);
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .task-item {
    background-color: white;
    border-radius: 12px;
    padding: 15px;
    margin-bottom: 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  }
  
  .task-content {
    display: flex;
    align-items: center;
  }
  
  .task-icon .circle {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: #132446;
  }
  
  .task-description {
    margin-left: 15px;
  }
  
  .task-name {
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  .task-reward {
    display: flex;
    align-items: center;
  }
  
  .coin-icon {
    width: 20px;
    height: 20px;
    margin-right: 5px;
  }
  
  .action-button {
    padding: 10px 20px;
    border-radius: 8px;
    font-weight: bold;
    border: none;
    color: white;
    font-family: 'Arial', sans-serif;
    letter-spacing: 1px;
    cursor: pointer;
    text-transform: uppercase;
  }
  
  .start-button {
    background-color: #132446;
  }
  
  .claim-button {
    background-color: #4CAF50;
  }
  </style>
  