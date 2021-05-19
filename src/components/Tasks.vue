<template>
  <div v-for="task in taskList" :key="task.id">
    <Task
      :task="task"
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @remove-task="$emit('remove-task', task.id)"
    />
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  props: {
    taskList: Array,
  },
  components: { Task },
  methods: {},
  emits: ["toggle-reminder", "remove-task"],
};
</script>

<style scoped></style>
