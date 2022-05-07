<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="['task', task.reminder ? 'reminder' : '']"
  >
    <h3>
      {{ task.text }}
      <font-awesome-icon
        @click="$emit('delete-task', task.id)"
        icon="fa-solid fa-times"
        class="red"
      />
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "e-task",
  props: {
    task: Object,
  },
};
</script>

<style scoped>
.red {
  color: red;
}

.task {
  background-color: lightblue;
  padding: 1rem;
  margin: 0.5rem;
  border-radius: 3px;
}

.reminder {
  border-left: 6px solid #2196f3;
}
</style>