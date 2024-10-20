<template>
  <div class="mb-3">
    <label :for="id" class="form-label">{{ label }}</label>
    <input
        :type="type"
        :id="id"
        v-model="modelValue"
        class="form-control"
        :placeholder="placeholder"
        :required="required"
    />
  </div>
</template>

<script lang="ts" setup>
const props = defineProps({
  label: String,
  type: String,
  id: String,
  placeholder: String,
  modelValue: String,
  required: {
    type: Boolean,
    default: false
  }
});
</script>
