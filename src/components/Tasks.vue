<template>
  <div>
    <div :key="task.id" v-for="task in tasks">
      <e-task @toggle-reminder=" $emit('toggle-reminder', task.id) " @delete-task=" $emit('delete-task', task.id) " :task="task"></e-task>
    </div>
  </div>
</template>

<script>
import eTask from "./Task.vue"

export default {
  name: "e-tasks",
  components:{eTask},
  props: {
    tasks: Array,
  },
  emits: ['delete-task', 'toggle-reminder']
};
</script>