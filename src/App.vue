<template>
  <TheHeader />

  <main>
    <AppBanner />
    <AppOrder />
  </main>
  <TheFooter />
</template>
<script setup>
import TheHeader from "./components/TheHeader.vue";
import TheFooter from "./components/TheFooter.vue";
import AppBanner from "./components/AppBanner.vue";
import AppOrder from "./components/AppOrder.vue";
</script>
