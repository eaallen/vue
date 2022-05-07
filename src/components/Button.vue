<template>
  <button @click="$emit('btn-click')" :style="{background: color}" class="btn">
    <slot />
  </button>
</template>

<script>
export default {
  name: "eButton",
  props: {
    color: String
  },
};

</script>
