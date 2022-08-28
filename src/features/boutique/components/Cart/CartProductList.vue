<script setup lang="ts">
import CartProduct from './CartProduct.vue';
import type { ProductCartInterface } from "@/interfaces";

defineProps<{
    cart: ProductCartInterface[]
}>()

const emit = defineEmits<{
    (e: 'removeProductFromCart', productId: string): void
}>()

</script>

<template>

    <div class="d-flex flex-column">
        <CartProduct v-for="product in cart" :product="product" :key="product._id" @remove-product-from-cart="emit('removeProductFromCart', $event)"/>   
    </div>

</template>

<style scoped lang="scss">
</style>