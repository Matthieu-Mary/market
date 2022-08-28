<script setup lang="ts">
import product from "@/data/product";
import type { ProductCartInterface } from "@/interfaces";

    const props = defineProps<{
        product: ProductCartInterface;
    }>()

    const emit = defineEmits<{
        (e: 'removeProductFromCart', productId: number): void
    }>()

    console.log(product);

</script>

<template>

    <div class="product mb-10 p-10 d-flex align-items-center">
        <strong class="mr-10">{{ props.product.title }}</strong>
        <span class="flex-fill mr-10">x {{ props.product.quantity }}</span>
        <span class="mr-10">{{ props.product.price }}€</span>
        <button class="btn btn-danger" @click="emit('removeProductFromCart', props.product.id)">Supprimer</button>
    </div>

</template>

<style scoped lang="scss">
    .product {
        border: var(--border);
        border-radius: var(--border-radius);
        background-color: var(--gray-1);
    }
</style>