<script setup lang="ts">
import ShopProduct from './ShopProduct.vue';
import type { ProductInterface } from "@/interfaces"

defineProps<{
    products: ProductInterface[]
}>()

const emit = defineEmits<{
    (e: 'addProductToCart', productId: string):void
}>()

</script>

<template>
    <div class="grid p-20">
        <ShopProduct  
        v-for="product in products" 
        :key="product._id"
        :product="product" 
        @add-product-to-cart='emit("addProductToCart", $event)'/>
    </div>
</template>

<style scoped lang="scss">
    @use '@/assets/scss/mixin' as m;
    .grid {
        display: grid;
        grid-template-columns: 1fr;
        @include m.md {
            grid-template-columns: 1fr 1fr;
        }
        @include m.lg {
            grid-template-columns: 1fr 1fr 1fr;
        }
        @include m.xl {
            grid-template-columns: 1fr 1fr 1fr 1fr;
        }
        grid-auto-rows: 400px;
        gap: 20px
    }
</style>