<template>
  <div class="container">
    <Header title="Task Tracker" />
    <AddTask />
    <Tasks
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Task 1",
        day: "March 1st at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Task 2",
        day: "March 2st at 2:30pm",
        reminder: false,
      },
      {
        id: 3,
        text: "Task 3",
        day: "March 3st at 2:30pm",
        reminder: true,
      },
      {
        id: 4,
        text: "Task 4",
        day: "March 4st at 2:30pm",
        reminder: false,
      },
    ];
  },
  methods: {
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => ({
        ...task,
        reminder: task.id === id ? !task.reminder : task.reminder,
      }));
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
