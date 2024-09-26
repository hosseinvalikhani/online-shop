<script setup>
const props = defineProps(["item", "supply"]);
const emit = defineEmits(["updateQuantity"]);
</script>

<template>
  <!-- {{ props.item }} -->
  <img :src="props.item.url" alt="" class="w-12 h-12 rounded-md" />
  {{ props.item.name }}
  {{ props.item.quantity }}
  <div class="flex items-center justify-center gap-4">
    <button
      @click="$emit('update:quantity', props.item.quantity - 1)"
      :disabled="props.item.quantity <= 1"
    >
      <img
        class="w-[20px] h-[20px] bg-white"
        src="./../assets/img/minus-circle-svgrepo-com.svg"
        alt=""
        :class="props.item.quantity <= 1 ? 'opacity-45' : ''"
      />
    </button>
    <p>{{ props.item.quantity }}</p>
    <button
      @click="$emit('update:quantity', props.item.quantity + 1)"
      :disabled="props.item.quantity >= props.supply"
    >
      <img
        class="w-[20px] h-[20px] bg-white"
        src="./../assets/img/plus-svgrepo-com.svg"
        alt=""
        :class="props.item.quantity >= props.supply ? 'opacity-45' : ''"
      />
    </button>
  </div>
</template>
