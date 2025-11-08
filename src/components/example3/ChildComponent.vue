<template>
  <div>
    <p>{{ message }}</p>
    <button @click="sendEvent">Send Event</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  message: String
});

const emit = defineEmits(['custom-event']);

const sendEvent = () => {
  emit('custom-event', 'Hello from child');
};
</script>