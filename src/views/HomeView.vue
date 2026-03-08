<script setup>

import { onMounted,onUnmounted } from "vue"
import CarouselBanner from "../components/CarouselBanner.vue"
import ProductCard from "../components/ProductCard.vue"

const props = defineProps({
products:Array
})

onMounted(()=>{
console.log("HomeView mounted — " + props.products.length + " products loaded")
})

onUnmounted(()=>{
console.log("HomeView unmounted")
})

</script>

<template>

<div class="max-w-6xl mx-auto px-6">

  <CarouselBanner :products="products" />

  <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mt-8">

    <ProductCard
      v-for="p in products"
      :key="p.id"
      :product="p"
    />

  </div>

</div>

</template>