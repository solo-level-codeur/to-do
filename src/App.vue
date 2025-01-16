<template>
  <div class="app">
    <h1>Ma Todo List 🧙🧙</h1>
    <!-- Composant pour ajouter une nouvelle tâche -->
    <TodoInput @add-task="addTask" />

    <!-- Composant pour afficher la liste des tâches -->
    <TodoList
      :tasks="tasks"
      @toggle-task="toggleTask"
      @delete-task="deleteTask"
    />
    
    <footer><h3>Fait avec ❤️ et beaucoup de ☕☕☕☕☕</h3></footer>
  </div>
</template>

<script>
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoInput,
    TodoList,
  },
  data() {
    return {
      tasks: [
        {
          title: 'Tâche à faire',
          completed: false,
          date: Date.now(), 
        },
      ],
    };
  },
  methods: {
    // Ajouter une nouvelle tâche
    addTask(taskTitle) {
      this.tasks.push({
        title: taskTitle,
        completed: false,
        date: Date.now(), // Enregistre la date de création
      });
      this.sortTasks();
    },

    // boutons de la TODO 2.0
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
      this.sortTasks();
    },

    // Supprimer une tâche
    deleteTask(index) {
      this.tasks.splice(index, 1);
      this.sortTasks();
    },

   
sortTasks() {
  this.tasks.sort((a, b) => {

    if (a.completed === b.completed) {
      return b.date - a.date;
    }
   
    return a.completed ? 1 : -1;
  });
}
  },
};
</script>

<style scoped>
body {
  background-color: rgb(42, 129, 216);
  color: rgb(0, 0, 0);
}

.app {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
  background-color: aliceblue;
  height: auto;
  padding: 20px;
  border-radius: 30px;
}

h1 {
  color: rgb(1, 8, 13);
}

footer {
  color: rgb(1, 8, 13);
  position: absolute;
  color: aliceblue;
  top: 90%;
  left: 50%;
  transform: translate(-50%, -50%);
}

/* Dans TodoList.vue, modifiez/ajoutez ces styles */
.task-item.completed {
  background-color: #e0e0e0;
  order: 1; /* Force les éléments complétés à aller en bas */
}

.task-item.completed .task-title {
  text-decoration: line-through;
  color: #666;
}

.todo-list {
  display: flex;
  flex-direction: column;
  text-align: left;
  margin: 20px 0;
}
</style>
