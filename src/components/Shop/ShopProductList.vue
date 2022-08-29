<script setup lang="ts">
import ShopProduct from "./ShopProduct.vue";
import type { ProductInterface } from "@/interfaces";

defineProps<{
  products: ProductInterface[];
}>();

const emit = defineEmits<{
  (e: "addProductToCart", productId: number): void;
}>();
</script>

<template>
  <div class="grid p-20">
    <ShopProduct
      v-for="product in products"
      :product="product"
      @add-product-to-cart="emit('addProductToCart', $event)"
    />
  </div>
</template>

<style scoped lang="scss">
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-auto-rows: 400px;
  gap: 20px;
}
</style>
