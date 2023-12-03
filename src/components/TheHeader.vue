<template>
  <header class="header">
    <div class="container">
      <nav class="header-container">
        <a href="#" class="logo">LoremIpsum.<span>Net</span></a>

        <button
          class="btn-menu"
          :class="{ opened: visibleMenu }"
          @click="openMenu"
        >
          <svg width="70" height="70" viewBox="0 0 100 100">
            <path
              class="line line1"
              d="M 20,29.000046 H 80.000231 C 80.000231,29.000046 94.498839,28.817352 94.532987,66.711331 94.543142,77.980673 90.966081,81.670246 85.259173,81.668997 79.552261,81.667751 75.000211,74.999942 75.000211,74.999942 L 25.000021,25.000058"
            />
            <path class="line line2" d="M 20,50 H 80" />
            <path
              class="line line3"
              d="M 20,70.999954 H 80.000231 C 80.000231,70.999954 94.498839,71.182648 94.532987,33.288669 94.543142,22.019327 90.966081,18.329754 85.259173,18.331003 79.552261,18.332249 75.000211,25.000058 75.000211,25.000058 L 25.000021,74.999942"
            />
          </svg>
        </button>

        <div class="menu-container" :class="{ opened: visibleMenu }">
          <button class="btn-mobile-close" type="button" @click="closeMenu">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-x"
              viewBox="0 0 16 16"
            >
              <path
                d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708"
              />
            </svg>
          </button>
          <ul class="menu">
            <li class="menu-item menu-item_active">
              <a href="#" class="menu-link">Бизнес</a>
            </li>
            <li class="menu-item">
              <a href="#" class="menu-link">О нас</a>
            </li>
            <li class="menu-item"><a href="#" class="menu-link">Цены</a></li>
            <li class="menu-item">
              <a href="#" class="menu-link">Оформить заказ</a>
            </li>
          </ul>
        </div>
        <div v-if="visibleMenu" @click="closeMenu" class="menu-backdrop"></div>
      </nav>
    </div>
  </header>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const visibleMenu = ref(false);

onMounted(() => {
  window.addEventListener("resize", closeMenu);
});

onUnmounted(() => {
  window.removeEventListener("resize", closeMenu);
});

const openMenu = () => {
  visibleMenu.value = true;

  document.body.style.overflow = "hidden";
};
const closeMenu = () => {
  visibleMenu.value = false;
  document.body.style.overflow = "";
};
</script>
