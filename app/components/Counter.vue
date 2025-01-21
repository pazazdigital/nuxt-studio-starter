<template>
  <div>
    <h3 class="text-3xl">Counter: {{ count }}</h3>
    <div class="space-x-4">
      <button @click="increment" class="btn">Increment</button>
      <button @click="decrement" class="btn">Decrement</button>
    </div>
  </div>
</template>

<script setup lang="ts">
const count = ref(0);

const increment = () => {
  count.value++;
};

const decrement = () => {
  count.value--;
};
</script>

<style>
.btn {
  @apply bg-blue-500 text-white px-4 py-2 rounded;
}
</style>
