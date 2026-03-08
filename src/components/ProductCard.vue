<script setup>

import { useRouter } from "vue-router"
import { onMounted,onUnmounted } from "vue"

const props = defineProps({
  product:Object
})

const router = useRouter()

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

<div class="card bg-base-100 shadow">

  <figure>
    <img
      :src="product.image"
      class="h-60 w-full object-cover"
    />
  </figure>

  <div class="card-body">

    <h2 class="card-title">
      {{ product.name }}
    </h2>

    <button
      class="btn btn-primary"
      @click="goToProduct"
    >
      View Product
    </button>

  </div>

</div>

</template>