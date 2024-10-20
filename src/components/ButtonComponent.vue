<template>
  <button :class="btnClass" @click="$emit('click')">
    <slot />
  </button>
</template>

<script lang="ts" setup>
const props = defineProps({
  btnClass: {
    type: String,
    default: 'btn btn-primary'
  }
});
</script>

<style scoped>
button {
  margin: 0.5rem;
}
</style>
