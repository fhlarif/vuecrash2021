<template >
  <div class="grid justify-center">
    <Header @toggle-add-task="toggleAddTask" 
    :showAddTask='showAddTask'
    title="Task Tracker" />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-this-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

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
    toggleAddTask() {
      
      this.showAddTask = !this.showAddTask;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },

    deleteTask(id) {
      if (confirm("Are you sure")) {
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
        id: "1",
        text: "Doctor Appointment",
        day: "March 3rd at 1.40pm",
        reminder: false,
      },
      {
        id: "2",
        text: "Meeting at School",
        day: "March 3rd at 2.40pm",
        reminder: true,
      },
      {
        id: "3",
        text: "Food Shopping",
        day: "March 3rd at 1.40pm",
        reminder: false,
      },
    ];
  },
};
</script>

