<script setup>

import { useRouter } from "vue-router"
import { computed, onMounted,onUnmounted } from "vue"

const props = defineProps({
  product:Object
})

const router = useRouter()

const finalPrice = computed(()=>{
  const discountAmount = (props.product.price * props.product.discount) / 100
  return Math.round((props.product.price - discountAmount) * 100) / 100
})

function goToProduct(){
  router.push("/product/" + props.product.id)
}

onMounted(()=>{
  console.log("ProductCard mounted")
})

onUnmounted(()=>{
  console.log("ProductCard unmounted")
})

</script>

<template>

<div class="card surface-card shadow-sm hover:shadow-lg transition-shadow duration-300 rounded-2xl overflow-hidden">

  <figure class="relative bg-slate-50">
    <img
      :src="product.image"
      class="h-60 w-full object-cover"
    />
    <span
      v-if="product.badge"
      class="badge badge-info border-0 text-white absolute top-3 left-3"
    >
      {{ product.badge }}
    </span>
  </figure>

  <div class="card-body">

    <h2 class="card-title text-slate-900">
      {{ product.name }}
    </h2>

    <p class="text-sm text-slate-500 min-h-10">
      {{ product.description }}
    </p>

    <div class="flex items-center gap-2">
      <span class="text-lg font-bold text-slate-900">${{ finalPrice }}</span>
      <span
        v-if="product.discount > 0"
        class="text-sm text-slate-400 line-through"
      >
        ${{ product.price }}
      </span>
      <span
        v-if="product.discount > 0"
        class="badge badge-success badge-sm text-white border-0"
      >
        -{{ product.discount }}%
      </span>
    </div>

    <div class="flex gap-2 flex-wrap">
      <span
        v-for="tag in product.tags"
        :key="tag"
        class="badge badge-outline text-xs"
      >
        {{ tag }}
      </span>
    </div>

    <button
      class="btn btn-info text-white rounded-full"
      @click="goToProduct"
    >
      View Product
    </button>

  </div>

</div>

</template>
