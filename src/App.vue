<template>
  <div class="app">
    <h1>Ma Todo List 🧙🧙 </h1>
    <!-- Composant pour ajouter une nouvelle tâche -->
    <TodoInput @add-task="addTask" />
    
    <!-- Composant pour afficher la liste des tâches -->
    <TodoList 
      :tasks="tasks" 
      @toggle-task="toggleTask" 
      @delete-task="deleteTask" 
    />
    <footer><h3>Fais avec ❤️ et beaucoup de ☕☕☕☕☕</h3></footer>
  </div>


</template>

<script>
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
  name: "App",
  components: {
    TodoInput,
    TodoList,
  },
  data() {
    return {
      tasks: [
        {
          title: "Tâche à faire",
          completed: false,
          date: Date.now(), // Exemple de date initiale
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
        date: Date.now(), // On enregistre la date de création
      });
    },

    // Basculer l'état "terminée" d'une tâche
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },

    // Supprimer une tâche
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
body{
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
  color:rgb(1, 8, 13);
}
footer{
  color: rgb(1, 8, 13);
  position: absolute;
  color: aliceblue;
  top: 90%;
  left: 50%;
  transform: translate(-50%, -50%);
}

</style>
