<script setup>

import { ref, computed } from "vue";
import Navbar from "./components/Navbar.vue"
const products = ref([
  {
    "id": 1,
    "name": "Cozy Sneakers",
    "description": "High-quality sneakers that go with everything you wear.",
    "image": "https://i.stpost.com/rocket-dog-mellow-cozy-sneakers-for-women~a~1aruy_4~1500.1.jpg",
    "badge": "NEW",
    "price": 120,
    "discount": 20,
    "stock": 10,
    "tags": ["Fashion", "Casual", "Sport"]
  },
  {
    "id": 2,
    "name": "Running Shoes",
    "description": "Built for speed and comfort on any terrain.",
    "image": "https://sportruns.com/media/How-to-Choose-the-Right-Trail-Running-Shoes-for-Your-Terrain-Trail-Running-Shoe-Features-for-Different-Terrains.jpg",
    "badge": "",
    "price": 90,
    "discount": 10,
    "stock": 5,
    "tags": ["Sport", "Running"]
  },
  {
    "id": 3,
    "name": "Casual Boots",
    "description": "Rugged boots for everyday adventures.",
    "image": "https://w7.pngwing.com/pngs/253/388/png-transparent-fashion-boot-shoe-knee-high-boot-leather-casual-shoes-leather-fashion-outdoor-shoe.png",
    "badge": "SALE",
    "price": 150,
    "discount": 0,
    "stock": 8,
    "tags": ["Casual", "Winter"]
  },
  {
    "id": 4,
    "name": "Flip Flops",
    "description": "Light and breezy for sunny days.",
    "image": "https://tse4.mm.bing.net/th/id/OIP.Z1eF1QecZP2NtFAjZeykqAHaJ4?rs=1&pid=ImgDetMain&o=7&rm=3",
    "badge": "",
    "price": 30,
    "discount": 50,
    "stock": 20,
    "tags": ["Summer", "Casual"]
  }
]
);

function buyProduct(id)
{
  const product = products.value.find(product => product.id == id);
  if(product && product.stock > 0)
  {
    product.stock--;
  }

}
const totalStock = computed(()=>{
  return products.value.reduce((sum,p)=> sum + p.stock ,0)
})
</script>

<template>

<Navbar :totalStock="totalStock" />

<router-view
:products="products"
@buy="buyProduct"
/>

</template>