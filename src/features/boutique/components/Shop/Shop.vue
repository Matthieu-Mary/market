<script setup lang="ts">
import ShopProductList from './ShopProductList.vue';
import type { FiltersInterface, FilterUpdate, ProductInterface } from "@/interfaces";
import ShopFilters from './ShopFilters.vue'

defineProps<{
    products: ProductInterface[],
    filters: FiltersInterface
}>()

const emit = defineEmits<{
    (e: 'addProductToCart', productId: string):void
    (e: 'updateFilter', updateFilter: FilterUpdate):void
}>()

</script>

<template>
    <div class="d-flex flex-row">
        <ShopFilters 
        class="shop-filter" 
        :filters="filters" 
        :nbr-of-products="products.length"
        @update-filter="emit('updateFilter', $event)" 
        />
        <ShopProductList 
        class="flex-fill scrollable" 
        :products="products" 
        @add-product-to-cart='emit("addProductToCart", $event)' 
        />
    </div>
</template>


<style scoped lang="scss">

.scrollable {
    overflow-y: auto;
    height: calc(100vh - 96px);
}
.shop-filter {
    flex: 0 0 200px;
}
</style>