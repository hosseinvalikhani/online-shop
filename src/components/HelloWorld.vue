<script setup lang="ts">
import { ref } from "vue";

interface info {
  url: string;
  name: string;
  description: string;
}
let mobileInfo = ref<info[]>([
  {
    url: "/src/assets/img/iphone13pro.webp",
    name: "iPhone 13 Pro",
    description:
      "Apple's premium phone with A15 Bionic chip and advanced camera features.",
  },
  {
    url: "/src/assets/img/honorX7B.webp",
    name: "Honor X7B",
    description:
      "Affordable device with a large display and long battery life.",
  },
  {
    url: "/src/assets/img/honorX9A.webp",
    name: "Honor X9A",
    description: "Mid-range phone with curved OLED display and fast charging.",
  },
  {
    url: "/src/assets/img/honorX9B.webp",
    name: "Honor X9B",
    description:
      "Stylish design with high durability and powerful performance.",
  },
  {
    url: "/src/assets/img/honor90.webp",
    name: "Honor 90",
    description:
      "Latest flagship phone with a 200MP camera and AI-enhanced photography.",
  },
  {
    url: "/src/assets/img/s21ultra.webp",
    name: "Samsung Galaxy S21 Ultra",
    description:
      "Samsung's top-tier model with a 108MP camera and 100x Space Zoom.",
  },
]);
</script>

<template>
  <ul class="grid grid-cols-1 bg-red-100">
    <li v-for="(item, index) in mobileInfo" :key="index">
      {{ item.url }}
      <img :src="item.url" alt="" class="w-40 h-40" />
      <p>{{ item.name }}</p>
    </li>
  </ul>
</template>

<style scoped></style>
