<template>
    <div class="todo-input">
      <input 
        type="text" 
        v-model="taskTitle" 
        placeholder="Ajouter une nouvelle tâche..." 
        @keyup.enter="submitTask" 
      />
      <button @click="submitTask">Ajouter</button>
    </div>
  </template>
  
  <script>
  export default {
    name: "TodoInput",
    data() {
      return {
        taskTitle: "", // Texte de la nouvelle tâche
      };
    },
    methods: {
      submitTask() {
        if (this.taskTitle.trim() !== "") {
          // Émet un événement vers le parent avec le titre de la tâche
          this.$emit("add-task", this.taskTitle.trim());
          // Réinitialise le champ de texte
          this.taskTitle = "";
        }
      },
    },
  };
  </script>
  
  <style>
  .todo-input {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
  }
  
  input {
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 4px;
    width: 300px;
  }
  
  button {
    padding: 10px 15px;
    font-size: 16px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  </style>
  