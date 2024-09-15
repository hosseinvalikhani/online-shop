<script setup>
import { ref } from "vue";

const basket = ref([]);

const mobileInfo = ref([
  {
    url: "/src/assets/img/iphone13pro.webp",
    name: "iPhone 13 Pro",
    description:
      "Apple's premium phone with A15 Bionic chip and advanced camera features.",
    supply: 10,
  },
  {
    url: "/src/assets/img/honorX7B.webp",
    name: "Honor X7B",
    description:
      "Affordable device with a large display and long battery life.",
    supply: 10,
  },
  {
    url: "/src/assets/img/honorX9A.webp",
    name: "Honor X9A",
    description: "Mid-range phone with curved OLED display and fast charging.",
    supply: 10,
  },
  {
    url: "/src/assets/img/honorX9B.webp",
    name: "Honor X9B",
    description:
      "Stylish design with high durability and powerful performance.",
    supply: 10,
  },
  {
    url: "/src/assets/img/honor90.webp",
    name: "Honor 90",
    description:
      "Latest flagship phone with a 200MP camera and AI-enhanced photography.",
    supply: 10,
  },
  {
    url: "/src/assets/img/s21ultra.webp",
    name: "Samsung Galaxy S21 Ultra",
    description:
      "Samsung's top-tier model with a 108MP camera and 100x Space Zoom.",
    supply: 10,
  },
]);

const isMobileInBasket = (index) => {
  // Get the name of the mobile at the specified index
  const mobileName = mobileInfo.value[index]?.name;

  // Check if the basket includes this mobile name
  return basket.value.some((basketItem) => basketItem.name === mobileName);
};
const basketIndex = (index) => {
  // Get the name of the mobile at the specified index
  const mobileName = mobileInfo.value[index]?.name;
  // Check if the basket includes this mobile name
  return basket.value.findIndex((basketItem) => basketItem.name === mobileName);
};

function addToBasket(index) {
  console.log(basket.value);
  console.log(mobileInfo.value[index]?.name);

  const existingItem = isMobileInBasket(index);
  let indexInBasket = basketIndex(index);
  mobileInfo.value[index].supply--;

  console.log(mobileInfo.value[index].supply);
  if (existingItem) {
    console.log(indexInBasket);
    // If the item exists in the basket, increase the quantity
    basket.value[indexInBasket].quantity++;
  } else {
    // If the item does not exist, create the object and push it to the basket
    const newItem = {
      url: mobileInfo.value[index]?.url,
      name: mobileInfo.value[index]?.name,
      quantity: 1, // Set initial quantity to 1
    };
    basket.value.push(newItem);
  }

  console.log(basket.value); // Log the basket to check the items
}
// function addToBasket(index) {
//   console.log("is", isMobileInBasket(index));
// }
</script>

<template>
  <ul class="grid grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-4">
    <li
      v-for="(item, index) in mobileInfo"
      :key="index"
      class="flex flex-col border-black border-2"
    >
      <img :src="item.url" alt="" class="rounded-md" />
      <button
        class="mx-2 py-2 bg-blue-200 active:bg-blue-700"
        @click="addToBasket(index)"
      >
        افزودن به سبد خرید
      </button>
      <p>{{ item.name }}</p>
      <p>{{ item.description }}</p>
    </li>
  </ul>
</template>

<style scoped></style>
