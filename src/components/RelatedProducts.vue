<!-- <script setup>
const props = defineProps([
"products",
"finalPrice"
])
</script>
<template>
    
<h2 class="text-2xl font-bold mb-6">
Related Products
</h2> 

<div class="grid grid-cols-1 md:grid-cols-3 gap-8">

  <div
    v-for="item in products"
    class="card bg-base-100 shadow"
  >

    <figure>
      <img
        :src="item.image"
        class="h-50 w-full object-contain"
      />
    </figure>

    <div class="card-body">

      <h2 class="card-title">
        {{ item.name }}
      </h2>

      <p
        v-if="item.discount > 0"
        class="line-through text-gray-400"
      >
        ${{ item.price }}
      </p>

      <p class="font-bold text-primary">
        ${{ finalPrice(item) }}
      </p>

    </div>

  </div>

</div>
</template> -->