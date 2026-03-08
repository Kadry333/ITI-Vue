<script setup>

import { computed } from "vue"
import { useRoute } from "vue-router"
import ProductDetails from "../components/ProductDetails.vue"
import ProductCard from "../components/ProductCard.vue"

const props = defineProps({
  products:Array
})

const emit = defineEmits(["buy"])

function buy(id){
  emit("buy", id)
}
const route = useRoute()

const product = computed(()=>{
  return props.products.find(p => p.id == route.params.id)
})

const related = computed(()=>{
  return props.products.filter(p => p.id != route.params.id)
})

</script>

<template>

<div>

  <ProductDetails
    :product="product"
    @buy = "buy"
  />

  <section class="mt-10">
    <div class="flex items-end justify-between mb-5">
      <h2 class="text-xl md:text-2xl font-bold text-slate-900">Related Products</h2>
      <span class="text-sm text-slate-500">{{ related.length }} options</span>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <ProductCard
        v-for="p in related"
        :key="p.id"
        :product="p"
      />
    </div>
  </section>

</div>

</template>
