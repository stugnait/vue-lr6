<template>
  <div class="mt-4">
    <h5 class="mb-3">Participants</h5>
    <table class="table table-bordered bg-white">
      <thead>
      <tr>
        <th>#</th>
        <th>Name</th>
        <th>Date of Birth</th>
        <th>Email</th>
        <th>Phone</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(participant, index) in participants" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ participant.name }}</td>
        <td>{{ participant.dob }}</td>
        <td>{{ participant.email }}</td>
        <td>{{ participant.phone }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts" setup>
import { defineProps } from 'vue';

const props = defineProps({
  participants: {
    type: Array,
    default: () => []
  }
});
</script>