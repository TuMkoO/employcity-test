<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="56"
    height="55"
    viewBox="0 0 56 55"
    fill="none"
    v-html="path"
  ></svg>
</template>
<script setup>
import icons from "../icons";

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
});

const path = icons[props.name];
</script>
