<template>
  <div class="form-select" :class="{ open: showOptions }">
    <select name="type" v-model="select">
      <option v-for="(opt, idx) in options" :key="idx" :value="opt.value">
        {{ opt.name }}
      </option>
    </select>
    <div>
      <div @click="toggleSelect" class="form-select__title">
        {{ selectedPlaceholder || placeholder }}
        <span @click.stop="toggleSelect" class="form-select__arr"></span>
      </div>
      <transition name="slide">
        <div v-show="showOptions" class="form-select__options">
          <button class="btn-mobile-close" type="button" @click="hideSelect">
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
          <simplebar class="options-wrapper" data-simplebar-auto-hide="false">
            <ul class="options">
              <li
                v-for="(opt, idx) in options"
                :key="idx"
                class="options-item"
                ref="activeOption"
                @click="selectOption($event, opt)"
              >
                {{ opt.name }}
              </li>
            </ul>
          </simplebar>
        </div>
      </transition>
    </div>
  </div>
</template>
<script setup>
import { ref, watch } from "vue";
import simplebar from "simplebar-vue";

const props = defineProps({
  options: {
    type: Object,
    required: true,
  },
  placeholder: {
    type: String,
    required: true,
  },
});

const activeOption = ref(null);
const select = ref("");
const selectedPlaceholder = ref("");
const showOptions = ref(false);

const selectOption = (event, option) => {
  select.value = option.value;
  selectedPlaceholder.value = option.name;

  showOptions.value = false;

  //styling by 'active' class
  //clear class
  const activeElements = document.querySelectorAll(".options-item.active");
  activeElements.forEach((element) => {
    element.classList.remove("active");
  });
  //add class
  event.target.classList.add("active");
};

const toggleSelect = () => {
  showOptions.value = !showOptions.value;
};
const hideSelect = (event) => {
  if (
    event.target.classList.contains("form-select__title") ||
    event.target.classList.contains("form-select__arr") ||
    event.target.classList.contains("form-select__options") ||
    event.target.classList.contains("options-item") ||
    event.target.classList.contains("options-wrapper")
  )
    return;

  showOptions.value = false;
};

watch(showOptions, (newVal) => {
  if (newVal) {
    document.addEventListener("click", hideSelect, true);
    document.body.classList.add("select-open");
  } else {
    document.removeEventListener("click", hideSelect, true);
    document.body.classList.remove("select-open");
  }
});
</script>
