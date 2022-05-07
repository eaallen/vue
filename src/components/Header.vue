<template>
  <header>
    <h1>{{ title }}</h1>
    <e-button @btn-click="$emit('show-form')" color="darkgreen"> Make a task </e-button>
  </header>
</template>

<script>
import EButton from "./Button.vue";
export default {
  name: "VHeader",
  props: {
    title: String,
  },
  components: {
    EButton,
  },
  emits:['show-form']
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
