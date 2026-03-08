<script setup>

import { computed, onMounted, onUnmounted } from "vue"

const props = defineProps({
  product: Object
})

const emit = defineEmits(["buy"])

const finalPrice = computed(() => {
  const discountAmount = (props.product.price * props.product.discount) / 100
  return Math.round((props.product.price - discountAmount) * 100) / 100
})

function buy() {
  emit("buy", props.product.id)
}

onMounted(() => {
  console.log("ProductDetails mounted")
})

onUnmounted(() => {
  console.log("ProductDetails unmounted")
})

</script>

<template>

<div class="mt-8">

  <div class="card lg:card-side surface-card shadow-sm rounded-3xl overflow-hidden">


    <figure class="p-6 md:p-8 w-full lg:w-1/2 bg-slate-50">

      <img
        :src="product.image"
        class="rounded-2xl w-full h-80 object-contain"
      />

    </figure>


    <div class="card-body lg:w-1/2 p-6 md:p-8">

      <div class="flex items-center gap-3">
        <h2 class="card-title text-3xl text-slate-900">
          {{ product.name }}
        </h2>
        <span
          v-if="product.badge"
          class="badge badge-info border-0 text-white"
        >
          {{ product.badge }}
        </span>
      </div>

      <p class="text-slate-600 text-base">
        {{ product.description }}
      </p>

      <div class="flex items-center gap-3">
        <span class="text-3xl font-extrabold text-slate-900">${{ finalPrice }}</span>
        <span
          v-if="product.discount > 0"
          class="text-base text-slate-400 line-through"
        >
          ${{ product.price }}
        </span>
        <span
          v-if="product.discount > 0"
          class="badge badge-success border-0 text-white"
        >
          Save {{ product.discount }}%
        </span>
      </div>

      <div class="flex flex-wrap gap-2">
        <span
          v-for="tag in product.tags"
          :key="tag"
          class="badge badge-outline"
        >
          {{ tag }}
        </span>
      </div>

      <div class="space-y-2 mt-1">
        <p class="text-sm font-medium text-slate-600">
          Stock: {{ product.stock }}
        </p>
        <progress
          class="progress progress-info w-full"
          :value="product.stock"
          max="20"
        />
      </div>

      <button
        class="btn btn-info text-white rounded-full w-44 mt-2"
        @click="buy"
        :disabled="product.stock === 0"
      >
        {{ product.stock === 0 ? "Out of Stock" : "Buy Now" }}
      </button>

      <p class="text-xs text-slate-500 mt-2">
        Fast delivery and free returns on all orders.
      </p>

    </div>

  </div>

</div>

</template>
