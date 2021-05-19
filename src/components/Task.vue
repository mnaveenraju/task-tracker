<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '','task']"
  >
    <div class="content">
      <div class="task-name">
        <h4>{{ task.name }}</h4>
        <div class="remove" @click="$emit('remove-task', task.id)">x</div>
      </div>
      <div class="task-day">
        <div>{{ task.day }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {},
  emits: ["toggle-reminder", "remove-task"],
};
</script>

<style scoped>
.task {
  margin: 5px 15px;
  display: flex;
  flex-direction: row;
  background-color: #f4f4f4;
  padding: 10px 20px;
}

.reminder {
  border-left: 2px solid green;
}

.content {
  width: 99%;
}

.task-name {
  display: flex;
  justify-content: space-between;
  margin: 0% 2% 0%;
}

.task-day {
  display: flex;
  margin: 0% 2% 2%;
}

.remove {
  color: red;
  cursor: pointer;
  font-weight: bold;
}

h4 {
    margin: 10px 0px;
}
</style>
