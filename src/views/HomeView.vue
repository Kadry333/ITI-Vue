<script setup>
import { onMounted, onUnmounted } from "vue"
import CarouselBanner from "../components/CarouselBanner.vue"
import ProductCard from "../components/ProductCard.vue"

const props = defineProps({
  products: Array
})

onMounted(() => {
  console.log("HomeView mounted - " + props.products.length + " products loaded")
})

onUnmounted(() => {
  console.log("HomeView unmounted")
})
</script>

<template>
  <div class="space-y-8">
    <section class="surface-card rounded-3xl p-6 md:p-8">
      <p class="text-sm uppercase tracking-[0.2em] text-sky-600 font-semibold">
        Seasonal Edit
      </p>
      <h1 class="text-3xl md:text-5xl font-extrabold leading-tight text-slate-900 mt-2">
        Find your next pair in under 60 seconds
      </h1>
      <p class="text-slate-600 mt-3 max-w-2xl">
        Clean styles, running essentials, and everyday comfort in one curated catalog.
      </p>
    </section>

    <CarouselBanner :products="products" />

    <section>
      <div class="flex items-end justify-between gap-3 mb-5">
        <h2 class="text-xl md:text-2xl font-bold text-slate-900">Shop All Products</h2>
        <span class="text-sm text-slate-500">{{ products.length }} items</span>
      </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <ProductCard
          v-for="p in products"
          :key="p.id"
          :product="p"
        />
      </div>
    </section>
  </div>
</template>
