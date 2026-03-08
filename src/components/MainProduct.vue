<!-- <script setup>
    const props = defineProps([
        "product",
        "productFinalPrice"
    ])
</script>
<template>
    <h2 class="text-2xl font-bold mb-6">
Main Product
</h2> 

 <div class="card lg:card-side bg-base-100 shadow-sm">

  <figure class="p-6">
    <img
      :src="product.image"
      class="w-150"
    />
  </figure>

  <div class="card-body">

    <h2 class="card-title">
      {{ product.name }}

      <div v-if="product.badge" class="badge badge-secondary">
        {{ product.badge }}
      </div>

    </h2>

    <p>
      {{ product.description }}
    </p>

    <p
      v-if="product.discount > 0"
      class="line-through text-gray-400"
    >
      ${{ product.price }}
    </p>

    <p class="text-xl text-primary font-bold">
      ${{ productFinalPrice }}
    </p>

    <div class="flex gap-2 mt-2">

      <span
        v-for="tag in product.tags"
        class="badge badge-outline"
      >
        {{ tag }}
      </span>

    </div>

    <div class="mt-4">
      <button class="btn btn-primary">
        Buy Now
      </button>
    </div>

  </div>

</div>
</template>  -->