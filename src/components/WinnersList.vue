<template>
  <div class="w-75">
    <h5>Winners</h5>
    <div v-if="winners.length > 0" class="mb-3">
      <span v-for="(winner, index) in winners" :key="index" class="badge bg-success text-white me-2 border border-success">
        {{ winner.name }}
      </span>
    </div>
    <div v-else class="text-muted">No winners selected yet</div>
  </div>
</template>

<script lang="ts" setup>
import { defineProps } from 'vue';

const props = defineProps({
  winners: {
    type: Array,
    default: () => []
  }
});
</script>