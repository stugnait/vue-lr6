<template>
  <div class="container mt-5">
    <div class="d-flex justify-content-between mb-4">
      <WinnersList :winners="winners" />
      <button @click="selectWinner" :disabled="winners.length >= 3 || participants.length === 0" class="btn btn-primary">New Winner</button>
    </div>
    <RegisterForm @addParticipant="addParticipant" />
    <ParticipantsTable :participants="participants" />
  </div>
</template>

<script lang="ts" setup>import { ref, onMounted, watch } from 'vue';
import WinnersList from "@/components/WinnersList.vue";
import RegisterForm from "@/components/RegisterForm.vue";
import ParticipantsTable from "@/components/ParticipantsTable.vue";

const participants = ref([]);
const winners = ref([]);

onMounted(() => {
  const storedParticipants = localStorage.getItem('participants');
  if (storedParticipants) {
    participants.value = JSON.parse(storedParticipants);
  }
});

watch(participants, (newParticipants) => {
  localStorage.setItem('participants', JSON.stringify(newParticipants));
});

function addParticipant(participant) {
  const exists = participants.value.some(p => p.email === participant.email);
  if (exists) {
    alert('Participant with this email already exists');
    return;
  }
  participants.value.push(participant);
}

function selectWinner() {
  if (participants.value.length > 0 && winners.value.length < 3) {
    let winner;
    do {
      const randomIndex = Math.floor(Math.random() * participants.value.length);
      winner = participants.value[randomIndex];
    } while (winners.value.includes(winner));
    winners.value.push(winner);
  }
}

</script>