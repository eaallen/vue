<template>
  <div id="app">
    <div class="container">
      <v-header @show-form="showFrom" title="Click Up But Better" />
      <e-add-task v-show="showingForm" @add-task="addTask" />
      <e-tasks
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask"
        :tasks="tasks"
      />
    </div>
  </div>
</template>

<script>
import VHeader from "./components/Header.vue";
import eTasks from "./components/Tasks.vue";
import eAddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: { VHeader, eTasks, eAddTask },
  data() {
    return {
      tasks: [],
      showingForm: false,
    };
  },
  methods: {
    showFrom() {
      console.log("--- show the form");
      this.showingForm = true;
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => {
        if (task.id === id) {
          task.reminder = !task.reminder;
        }
        return task;
      });
    },
    async addTask(task) {
      

      // option 1
      this.tasks.push(task);
      this.showingForm = false

      // vs

      // option 2
      // this.tasks = [...this.tasks, task]
    },
    async fetchTasks(){
      const res = await fetch('api/tasks')

      const data = await res.json()

      return data

    },
    async fetchTask(id){
      const res = await fetch(`api/tasks/${id}`)

      const data = await res.json()

      return data

    },
  },
  async created() {
    this.tasks = await this.fetchTasks()
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
