<template>
  <section class="order">
    <div class="container">
      <h2 class="order-title">Оформление <span>заказа</span></h2>
      <div class="order-subtitle">
        Перед заполнением формы ознакомьтесь с нашей схемой работы!
      </div>
      <div class="order__steps">
        <AppOrderStep icon="search" text="Lorem ipsum dolor sit amet" />
        <AppOrderStep icon="percent" text="Сonsecteturadipiscing elit" />
        <AppOrderStep icon="file" text="Sed do eiusmod tempor" />
        <AppOrderStep icon="message" text="Esse cillum dolore eu fugiat" />
        <AppOrderStep
          icon="money"
          text="Excepteur sint occaecat cupidatat non proident"
        />
      </div>
      <div class="order__form">
        <AppForm />
      </div>
    </div>
  </section>
</template>
<script setup>
import AppOrderStep from "./AppOrderStep.vue";
import AppForm from "./AppForm.vue";
</script>
