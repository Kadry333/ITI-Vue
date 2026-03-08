<script setup>

import { onMounted, onUnmounted } from "vue"

const props = defineProps({
  product: Object
})

const emit = defineEmits(["buy"])

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

<div class="max-w-6xl mx-auto mt-10">

  <div class="card lg:card-side bg-base-100 shadow-xl">


    <figure class="p-6 w-full lg:w-1/2">

      <img
        :src="product.image"
        class="rounded-xl w-full h-80 object-contain"
      />

    </figure>


    <div class="card-body lg:w-1/2">

      <h2 class="card-title text-2xl">
        {{ product.name }}
      </h2>

      <p class="text-gray-400">
        {{ product.description }}
      </p>

      <p class="mt-2">
        Stock: {{ product.stock }}
      </p>

      <button
        class="btn btn-primary w-40"
        @click="buy"
        :disabled="product.stock === 0"
      >
        {{ product.stock === 0 ? "Out of Stock" : "Buy Now" }}
      </button>

    </div>

  </div>

</div>

</template>