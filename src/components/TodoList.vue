<template>
    <div class="todo-list">
      <div 
        v-for="(task, index) in tasks" 
        :key="task.date" 
        :class="['task-item', { completed: task.completed }]"
      >
        <input 
          type="checkbox" 
          :checked="task.completed"
          @change="toggleTask(index)" 
        />
        <span class="task-title">{{ task.title }}</span>
        <button @click="deleteTask(index)" class="delete-btn">Supprimer</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TodoList',
    props: {
      tasks: Array,
    },
    methods: {
      // Déclencher l'événement de basculement de tâche
      toggleTask(index) {
        this.$emit('toggle-task', index);
      },
      // Déclencher l'événement de suppression de tâche
      deleteTask(index) {
        this.$emit('delete-task', index);
      },
    },
  };
  </script>
  
  <style scoped>
  .todo-list {
    text-align: left;
    margin: 20px 0;
  }
  
  .task-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #f3f4f6;
    padding: 10px;
    border-radius: 10px;
    margin-bottom: 10px;
    transition: all 0.3s ease;
  }
  
  .task-item.completed {
    background-color: #e0e0e0;
  }
  
  .task-title {
    flex-grow: 1;
    padding-left: 10px;
  }
  
  .task-item.completed .task-title {
    text-decoration: line-through;
    color: gray;
  }
  
  .delete-btn {
    background-color: red;
    color: white;
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .delete-btn:hover {
    background-color: darkred;
  }
  </style>
  
