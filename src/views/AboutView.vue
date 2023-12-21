<script setup>
  import { ref, computed } from 'vue';
  const first = ref('123');
  const last = ref('456');

  const fullName = computed({
    get() {
      return `${first.value} ${last.value}`;
    },
    set(newValue) {
      [first.value, last.value] = newValue.split(' ');
    },
  });
</script>

<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div class="flex flex-col w-[150px] gap-5 text-black">
      <input v-model="first" type="text">
      <input v-model="last" type="text">
    </div>
    <div class="flex flex-col gap-3">
      <p>output: {{ fullName }}</p>
      <p>first: {{ first }}</p>
      <p>last: {{ last }}</p>
    </div>
    <div>
      <button class="border px-5 py-2" type="button" @click="fullName = 'john wick'">john wick</button>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    @apply flex-col justify-center;
    min-height: 100vh;
    display: flex;
  }
}
</style>
