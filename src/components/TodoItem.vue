<template>
    <li :class="{ completed: task.completed }">
      <span @click="toggleTask" class="task-title">{{ task.title }}</span>
      <button @click="deleteTask" class="delete-button">❌</button>
    </li>
  </template>
  
  <script>
  export default {
    name: "TodoItem",
    props: {
      task: {
        type: Object,
        required: true,
      },
      index: {
        type: Number,
        required: true,
      },
    },
    methods: {
      // Marquer la tâche comme terminée ou non
      toggleTask() {
        this.$emit("toggle-task", this.index);
      },
  
      // Supprimer la tâche
      deleteTask() {
        this.$emit("delete-task", this.index);
      },
    },
  };
  </script>
  
  <style>
  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ddd;
  }
  
  .completed {
    text-decoration: line-through;
    color: #999;
  }
  
  .task-title {
    cursor: pointer;
    font-size: 18px;
  }
  
  .delete-button {
    background: none;
    border: none;
    color: red;
    font-size: 20px;
    cursor: pointer;
  }
  
  .delete-button:hover {
    color: #cc0000;
  }
  </style>
  