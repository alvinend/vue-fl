<template>
  <form @submit="onSubmit">
    <div>
      <label>Task</label>
      <input type="text" name="text" placeholder="Add Task" v-model="text" />
    </div>

    <div>
      <label>Day & Time</label>
      <input
        type="text"
        name="day"
        placeholder="Add Day & Time"
        v-model="day"
      />
    </div>

    <div>
      <label>Set Reminder</label>
      <input type="checkbox" name="reminder" v-model="reminder" />
    </div>

    <input type="submit" value="Save Task" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.text) {
        alert("Please add a task");
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };

      this.text = "";
      this.day = "";
      this.reminder = false;

      this.$emit("add-task", newTask);
    },
  },
};
</script>
