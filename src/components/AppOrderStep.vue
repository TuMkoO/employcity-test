<template>
  <div class="step">
    <div class="step-icon">
      <AppOrderStepIcon :name="icon" />
    </div>
    <div class="step-text">{{ text }}</div>
  </div>
</template>
<script setup>
import AppOrderStepIcon from "./AppOrderStepIcon.vue";

defineProps({
  text: {
    type: String,
    required: true,
  },
  icon: {
    type: String,
    required: true,
  },
});
</script>
