<template>
  <div class="bg-white rounded-lg shadow-md p-4 flex flex-col items-center">
    <router-link :to="{ name: 'product-details', params: { id: product.id } }">
      <img :src="product.thumbnail" :alt="product.title" class="w-full h-32 object-contain mb-4">
      <h3 class="text-lg font-semibold mb-2">{{ product.title }}</h3>
    </router-link>
    <p class="text-gray-700 text-sm mb-2">{{ product.category }}</p>
    <p class="text-xl font-bold text-red-600 mb-4">${{ product.price.toFixed(2) }}</p>
    <button @click="handleAddToCart" class="bg-orange-500 text-white px-4 py-2 rounded hover:bg-orange-600 w-full">
      Adicionar ao Carrinho
    </button>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import { useCartStore } from '../stores/cartStore';

const props = defineProps({
  product: Object
});

const { addToCart } = useCartStore();

const handleAddToCart = () => {
  addToCart(props.product);
  alert(`${props.product.title} adicionado ao carrinho!`);
};
</script>