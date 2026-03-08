<script setup>
import { onMounted, onUnmounted } from 'vue';

onMounted(() => console.log("AboutView mounted"));
onUnmounted(() => console.log("AboutView unmounted"));
</script>

<template>
  <div class="hero bg-base-200 min-h-[50vh] rounded-3xl">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold">Hello!</h1>
        <p class="py-6 text-xl">
          I'm <strong>Kareem Kadry</strong>, a student at <strong>ITI</strong>. 
          This is my Lab 2 for the VueJS Course.
        </p>
        <p class="text-gray-500">
          This store is a Multi-Page SPA built with Vue 3, Tailwind, and DaisyUI. 
          It demonstrates Props, Emits, Routing, and Lifecycle Hooks.
        </p>
      </div>
    </div>
  </div>
</template>