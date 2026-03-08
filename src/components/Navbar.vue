<script setup>

import { RouterLink } from "vue-router"
import { onMounted,onUnmounted } from "vue"

const props = defineProps({
  totalStock:Number
})

onMounted(()=>{
console.log("NavBar mounted")
})

onUnmounted(()=>{
console.log("NavBar unmounted")
})

</script>

<template>

<div class="navbar bg-base-200 px-6">


  <div class="navbar-start gap-6">

    <RouterLink to="/">Home</RouterLink>

    <RouterLink to="/product/1">Product</RouterLink>

    <RouterLink to="/about">About</RouterLink>

  </div>


  <div class="navbar-end">

    <div class="badge badge-primary text-sm p-3">
      Stock: {{ totalStock }}
    </div>

  </div>

</div>

</template>