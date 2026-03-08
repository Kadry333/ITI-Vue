<script setup>

import { onMounted, onUnmounted } from "vue"

onMounted(() => {
  console.log("CarouselBanner mounted")
})

onUnmounted(() => {
  console.log("CarouselBanner unmounted")
})

const props = defineProps({
  products: Array
})

</script>

<template>

<div class="max-w-6xl mx-auto mt-4">

  <div class="carousel w-full h-56 md:h-72 rounded-xl overflow-hidden">

    <div
      v-for="(p, index) in products"
      :key="p.id"
      :id="'slide' + index"
      class="carousel-item relative w-full"
    >

      <img
        :src="p.image"
        class="w-full h-full object-contain"
      />

      <div class="absolute flex justify-between transform -translate-y-1/2 left-5 right-5 top-1/2">

        <a
          :href="'#slide' + (index === 0 ? products.length - 1 : index - 1)"
          class="btn btn-circle btn-sm"
        >
          ❮
        </a>

        <a
          :href="'#slide' + (index === products.length - 1 ? 0 : index + 1)"
          class="btn btn-circle btn-sm"
        >
          ❯
        </a>

      </div>

    </div>

  </div>

</div>

</template>