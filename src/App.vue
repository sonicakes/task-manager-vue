<template>
  <div id="app">
    <div class="container">
      <Header title="Task Manager" @toggle-add-task="toggleAddTask" :showAddTask="showAddTask"/>
      <div v-if="showAddTask">
        <AddTask @add-task="addTask" />
      </div>
      <Tasks
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask"
        :tasks="tasks"
      />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
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
      showAddTask: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Vet Appointment",
        day: "March 1, 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Hair Appointment",
        day: "March 5, 12:30pm",
        reminder: false,
      },
      {
        id: 3,
        text: "Study Appointment",
        day: "March 12, 5:00pm",
        reminder: true,
      },
    ];
  },
};
</script>

<style></style>
