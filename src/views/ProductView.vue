<script setup>

import { computed } from "vue"
import { useRoute } from "vue-router"
import ProductDetails from "../components/ProductDetails.vue"
import ProductCard from "../components/ProductCard.vue"

const props = defineProps({
  products:Array
})

const route = useRoute()

const product = computed(()=>{
  return props.products.find(p => p.id == route.params.id)
})

const related = computed(()=>{
  return props.products.filter(p => p.id != route.params.id)
})

</script>

<template>

<div class="max-w-6xl mx-auto px-6">

  <ProductDetails
    :product="product"
    @buy="$emit('buy',$event)"
  />

  <h2 class="text-xl font-bold mt-10 mb-6">
    Related Products
  </h2>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-6">

    <ProductCard
      v-for="p in related"
      :key="p.id"
      :product="p"
    />

  </div>

</div>

</template>