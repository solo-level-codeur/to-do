<template>
    <div class="todo-input">
      <input 
        v-model="newTaskTitle" 
        @keyup.enter="addTask" 
        placeholder="Ajouter une nouvelle tâche..." 
        class="input-task"
      />
      <button @click="addTask" class="add-btn">Ajouter</button>
    </div>
  </template>
  
  <script>
  export default {
    name: "TodoInput",
    data() {
      return {
        newTaskTitle: '',
      };
    },
    methods: {
      addTask() {
        if (this.newTaskTitle.trim()) {
          this.$emit('add-task', this.newTaskTitle);
          this.newTaskTitle = '';
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .todo-input {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  .input-task {
    padding: 10px;
    font-size: 16px;
    width: 70%;
    border-radius: 10px;
    border: 1px solid #ccc;
  }
  
  .add-btn {
    padding: 10px;
    font-size: 16px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
  }
  
  .add-btn:hover {
    background-color: #45a049;
  }
  </style>
  
