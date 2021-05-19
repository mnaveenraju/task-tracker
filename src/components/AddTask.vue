<template>
  <div v-show="toggleAddTask">
    <form @submit="onSubmit">
      <div class="field n-m-t">
        <label for="name">Name</label>
        <input
          type="text"
          name="name"
          id="name"
          placeholder="Name"
          v-model="name"
        />
      </div>
      <div class="field">
        <label for="time">Day</label>
        <input
          type="text"
          name="day"
          id="day"
          placeholder="Day"
          v-model="day"
        />
      </div>
      <div class="checkbox">
        <input
          type="checkbox"
          name="reminder"
          id="reminder"
          v-model="reminder"
        />
        <label for="reminder">Set Reminder</label>
      </div>

      <Button type="submit" text="Create" bg-color="black" color="white" />
    </form>
  </div>
</template>

<script>
import Button from "./Button";
export default {
  name: "AddTask",
  components: { Button },
  props: {
    toggleAddTask: Boolean
  },
  data() {
    return {
      name: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit($event) {
      $event.preventDefault();
      if (!this.name) {
        alert('Please enter name of task');
        return
      }
      const newTask = {
        id: Math.floor(Math.random() * 100000),
        name: this.name,
        day: this.day,
        reminder: this.reminder,
      };
      //   console.log(newTask, $event);
      this.$emit("create-new-task", newTask);
      this.name = "";
      this.day = "";
      this.reminder = false;
    },
  },
  emits: ["create-new-task"],
};
</script>

<style>

form {
  display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.field {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin: 10px 0px;
}

.checkbox {
  margin: 10px 0px;
}

label {
  font-weight: bold;
}

input[type="text"] {
  padding: 10px;
  border: 2px solid;
  border-radius: 10px;
}

input[type="text"]:focus-visible {
  padding: 10px;
  border: 2px solid #739f9f;
  border-radius: 10px;
  outline: none;
}

.n-m-t {
  margin-top: unset;
}
</style>
