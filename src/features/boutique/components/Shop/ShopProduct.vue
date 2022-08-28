<script setup lang="ts">
import type { ProductInterface } from "@/interfaces"

    defineProps<{
        product: ProductInterface
    }>()

   const emit = defineEmits<{
        (e: 'addProductToCart', productId: string): void
    }>()

</script>

<template>
    <div class="product d-flex flex-column">
        <div class="product-image" :style="{ backgroundImage: `url(${product.image})` }"></div>
        <div class="p-10 d-flex flex-column">
            <h4>{{ product.title }}</h4>
            <p>{{ product.description }}</p>
            <div class="d-flex align-items-center">
                <strong class="flex-fill">{{ product.price }}€</strong>
                <button @click="emit('addProductToCart', product._id)" class="btn btn-primary">Ajouter au panier</button>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.product {
    background-color: white;
    border: var(--border);
    border-radius: var(--border-radius);
    .product-image {
        border-top-right-radius: var(--border-radius);
        border-top-left-radius: var(--border-radius);
        height: 250px;
        background-size: cover;
        background-position: center;
    }
}
    
</style>