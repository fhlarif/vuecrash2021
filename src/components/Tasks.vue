<template>
  <div v-for="task in tasks" :key="task.id" class="mt-5">
    <Task @toggle-reminder="$emit('toggle-reminder',task.id)" v-on:delete-task="$emit('delete-this-task',task.id)"  :task="task" />
  </div>
</template>

<script >
import Task from "./Task";

export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },

  components: {
    Task,
  },

  emits: ['delete-this-task','toggle-reminder'],
};
</script>