<template>
  <div class="header">
    <div>
      <h2>Task Tracker</h2>
    </div>
    <Button
      :text="toggleAddTask ? 'Close' : 'Add Task'"
      type="button"
      :bgColor="toggleAddTask ? 'red' :'green'"
      color="white"
      @button-click="$emit('add-task')"
    />
  </div>
</template>
<script>
import Button from "./Button";
export default {
  name: "Header",
  components: { Button },
  props: {
    toggleAddTask: Boolean,
  },
  emits: ["add-task"],
};
</script>
<style scoped>
button {
  width: 30%;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
