<template>
  <div class="task" @dblclick="$emit('toggle-reminder', task.id)">
    <h3>{{ task.text }}</h3>
    <p>{{ task.day }}</p>
    <span v-if="task.reminder">PING!!</span>
    <button @click="onDelete(task.id)">Delete</button>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
  },
};
</script>
