<template>
  <div class="card p-4 mb-4 bg-white">
    <h5 class="card-title">REGISTER FORM</h5>
    <p class="card-text">Please fill in all the fields.</p>
    <form @submit.prevent="handleSubmit">
      <div class="mb-3">
        <label for="name" class="form-label">Name</label>
        <input type="text" id="name" v-model="form.name" class="form-control" required placeholder="Enter user name" />
      </div>
      <div class="mb-3">
        <label for="dob" class="form-label">Date of Birth</label>
        <input type="date" id="dob" v-model="form.dob" class="form-control" :max="today" required placeholder="mm/dd/yyyy" />
      </div>
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <input type="email" id="email" v-model="form.email" class="form-control" required placeholder="Enter email" />
      </div>
      <div class="mb-3">
        <label for="phone" class="form-label">Phone Number</label>
        <input type="tel" id="phone" v-model="form.phone" class="form-control" required placeholder="Enter Phone number" />
      </div>
      <button type="submit" class="btn btn-primary">Save</button>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const today = new Date().toISOString().split('T')[0];
const form = ref({
  name: '',
  dob: '',
  email: '',
  phone: ''
});

const emit = defineEmits(['addParticipant']);

function handleSubmit() {
  // Валідація полів (напр. email і телефон через регекс)
  if (validateEmail(form.value.email) && validatePhone(form.value.phone)) {
    // Викидає подію додавання учасника
    emit('addParticipant', { ...form.value });
    // Очистити форму після додавання
    form.value = { name: '', dob: '', email: '', phone: '' };
  } else {
    console.error('Please enter valid email and phone number');
  }
}

function validateEmail(email: string): boolean {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailRegex.test(email);
}

function validatePhone(phone: string): boolean {
  const phoneRegex = /^\d{10}$/;
  return phoneRegex.test(phone);
}
</script>