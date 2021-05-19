<template>
  <!-- <div class="add-task"> -->
    <Header @add-task="addTask" class="m6" :toggleAddTask="toggleAddTask" />
    <AddTask class="m6" @create-new-task="createNewTask" :toggleAddTask="toggleAddTask" />
  <!-- </div> -->
  <Tasks
    :taskList="taskList"
    @toggle-reminder="toggleReminder"
    @remove-task="removeTask"
  />
</template>

<script>
import Header from "./components/Header";
import AddTask from "./components/AddTask";
import Tasks from "./components/Tasks";

export default {
  name: "App",
  components: {
    Header,
    AddTask,
    Tasks,
  },
  data() {
    return {
      taskList: [],
      toggleAddTask: true
    };
  },
  created() {
    this.taskList = [
      { id: 1, name: "Default Naveen", day: "today", reminder: true },
      { id: 2, name: "Default Naveen 2", day: "tomorrow", reminder: true },
    ];
  },
  methods: {
    addTask() {
      this.toggleAddTask = !this.toggleAddTask;
    },
    createNewTask(task) {
      console.log(task);
      this.taskList = [...this.taskList, task];
      console.log(this.taskList);
    },
    removeTask(id) {
      this.taskList = this.taskList.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      this.taskList = this.taskList.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
};
</script>

<style>
body {
  display: flex;
  justify-content: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  max-width: 420px;
  min-width: 320px;
  font-family: 'Roboto', sans-serif;
  border: 1px solid grey;
}

.add-task {
  display: flex;
  justify-content: space-between;
}

.m6 {
  margin: 5px 15px;
}
</style>
