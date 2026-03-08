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
<header class="sticky top-0 z-40">
  <div class="navbar surface-card rounded-2xl px-4 md:px-6 mt-3 md:mt-4 max-w-7xl mx-auto">
    <div class="navbar-start">
      <div class="dropdown md:hidden mr-2">
        <label tabindex="0" class="btn btn-ghost btn-circle">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h12M4 18h8" />
          </svg>
        </label>
        <ul tabindex="0" class="dropdown-content menu p-2 shadow bg-base-100 rounded-box w-44 z-50">
          <li><RouterLink to="/">Home</RouterLink></li>
          <li><RouterLink to="/product/1">Featured</RouterLink></li>
          <li><RouterLink to="/about">About</RouterLink></li>
        </ul>
      </div>
      <RouterLink to="/" class="font-extrabold text-lg tracking-tight text-slate-800">
        ShoeNest
      </RouterLink>
    </div>

    <div class="navbar-center hidden md:flex gap-2">
      <RouterLink to="/" custom v-slot="{ navigate, isActive }">
        <button
          class="btn btn-sm rounded-full px-5"
          :class="isActive ? 'btn-info text-white' : 'btn-ghost'"
          @click="navigate"
        >
          Home
        </button>
      </RouterLink>

      <RouterLink to="/product/1" custom v-slot="{ navigate, isActive }">
        <button
          class="btn btn-sm rounded-full px-5"
          :class="isActive ? 'btn-info text-white' : 'btn-ghost'"
          @click="navigate"
        >
          Featured
        </button>
      </RouterLink>

      <RouterLink to="/about" custom v-slot="{ navigate, isActive }">
        <button
          class="btn btn-sm rounded-full px-5"
          :class="isActive ? 'btn-info text-white' : 'btn-ghost'"
          @click="navigate"
        >
          About
        </button>
      </RouterLink>
    </div>

    <div class="navbar-end">
      <div class="badge badge-info text-white text-xs md:text-sm p-3 md:p-4 rounded-full border-0">
        Items In Stock: {{ totalStock }}
      </div>
    </div>
  </div>
</header>

</template>
