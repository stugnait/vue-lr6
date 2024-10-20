<template>
  <span class="badge bg-success text-white me-2 border border-success">
    {{ winner.name }}
  </span>
</template>

<script lang="ts" setup>
const props = defineProps({
  winner: Object
});
</script>
