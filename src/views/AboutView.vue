<script setup>
import { onMounted, onUnmounted } from 'vue';

onMounted(() => console.log("AboutView mounted"));
onUnmounted(() => console.log("AboutView unmounted"));
</script>

<template>
  <div class="surface-card min-h-[58vh] rounded-3xl p-6 md:p-10 flex items-center">
    <div class="max-w-3xl">
      <p class="text-sm uppercase tracking-[0.2em] text-sky-600 font-semibold">About This Project</p>
      <h1 class="text-4xl md:text-6xl font-extrabold text-slate-900 mt-2">Vue Store Lab</h1>
      <p class="py-6 text-lg md:text-2xl text-slate-700 leading-relaxed">
        I'm <strong>Kareem Kadry</strong>, an <strong>ITI</strong> student. This is Lab 2 for the Vue.js course.
      </p>
      <p class="text-slate-500 max-w-2xl">
        The app is a multi-page SPA built with Vue 3, Tailwind, and DaisyUI. It focuses on component composition, props, emits, router navigation, and lifecycle hooks.
      </p>
      <div class="mt-6 flex gap-3 flex-wrap">
        <span class="badge badge-outline p-4">Vue 3</span>
        <span class="badge badge-outline p-4">Tailwind CSS</span>
        <span class="badge badge-outline p-4">DaisyUI</span>
      </div>
    </div>
  </div>
</template>
