<template>
    <div class="todo-list">
      <div v-if="tasks.length === 0" class="empty-message">
        🎉 Aucune tâche pour l'instant. Ajoutez-en une !
      </div>
      <ul>
        <!-- Boucle pour afficher chaque tâche -->
        <TodoItem
          v-for="(task, index) in tasks"
          :key="index"
          :task="task"
          :index="index"
          @toggle-task="toggleTask"
          @delete-task="deleteTask"
        />
      </ul>
    </div>
  </template>
  
  <script>
  // On importe le composant TodoItem
  import TodoItem from './TodoItem.vue';
  
  export default {
    name: "TodoList",
    components: {
      TodoItem,
    },
    props: {
      tasks: {
        type: Array,
        required: true,
      },
    },
    methods: {
      // Émet un événement au parent pour basculer l'état d'une tâche
      toggleTask(index) {
        this.$emit("toggle-task", index);
      },
  
      // Émet un événement au parent pour supprimer une tâche
      deleteTask(index) {
        this.$emit("delete-task", index);
      },
    },
  };
  </script>
  
  <style>
  .todo-list {
    margin: 20px 0;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  .empty-message {
    text-align: center;
    color: #666;
    font-size: 16px;
  }
  </style>
  