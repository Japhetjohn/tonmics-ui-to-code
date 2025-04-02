<template>
    <div class="tasks-header">
      <h1 class="title">TASKS</h1>
      <h2 class="subtitle">GET REWARDS FOR COMPLETING QUESTS</h2>
      
      <div class="tab-container">
        <div 
          v-for="(tab, index) in tabs" 
          :key="index"
          :class="['tab', { active: activeTab === tab.id }]"
          @click="setActiveTab(tab.id)"
        >
          {{ tab.name }}
          <span v-if="tab.count > 0" class="tab-badge">{{ tab.count }}</span>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TasksHeader',
    props: {
      activeTab: {
        type: String,
        default: 'daily'
      }
    },
    data() {
      return {
        tabs: [
          { id: 'daily', name: 'DAILY TASKS', count: 1 },
          { id: 'tasks', name: 'TASKS', count: 1 },
          { id: 'special', name: 'SPECIAL', count: 1 }
        ]
      }
    },
    methods: {
      setActiveTab(tabId) {
        this.$emit('update-tab', tabId);
      }
    }
  }
  </script>
  
  <style scoped>
  .tasks-header {
    padding: 20px 0;
    position: relative;
  }
  
  .title {
    font-size: 36px;
    font-weight: bold;
    margin-bottom: 5px;
    font-style: italic;
    color: black;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
  }
  
  .subtitle {
    font-size: 18px;
    color: white;
    margin-bottom: 20px;
    font-weight: bold;
  }
  
  .tab-container {
    display: flex;
    background-color: #132446;
    border-radius: 8px;
    overflow: hidden;
  }
  
  .tab {
    flex: 1;
    text-align: center;
    padding: 12px 0;
    font-weight: bold;
    color: white;
    cursor: pointer;
    position: relative;
  }
  
  .tab.active {
    background-color: white;
    color: black;
  }
  
  .tab-badge {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    width: 20px;
    height: 20px;
    background-color: #ff4141;
    color: white;
    border-radius: 50%;
    font-size: 12px;
    margin-left: 5px;
  }
  </style>
  