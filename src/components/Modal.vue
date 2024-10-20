<template>
  <div class="modal fade show" style="display: block;" tabindex="-1">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">{{ title }}</h5>
          <button type="button" class="btn-close" @click="$emit('close')" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <slot />
        </div>
        <div class="modal-footer">
          <ButtonComponent @click="$emit('confirm')" btnClass="btn btn-primary">Confirm</ButtonComponent>
          <ButtonComponent @click="$emit('close')" btnClass="btn btn-secondary">Close</ButtonComponent>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import ButtonComponent from "@/components/ButtonComponent.vue";

const props = defineProps({
  title: String
});
</script>
