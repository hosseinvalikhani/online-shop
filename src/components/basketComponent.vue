<script setup>
const props = defineProps(["item"]);
</script>

<template>
  <ul class="grid grid-cols-1 gap-4 w-[400px]">
    <li>
      <img :src="item.url" alt="" class="w-12 h-12 rounded-md" />
      {{ item.name }}
      {{ item.quantity }}
    </li>
  </ul>
</template>
