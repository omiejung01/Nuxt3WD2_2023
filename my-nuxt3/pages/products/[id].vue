<template>
    <div>
        <ProductDetails :product="product" />

    </div>
</template>

<script setup lang="ts">
    const { id } = useRoute().params
    const uri = 'https://fakestoreapi.com/products/' + id

    // fetch singlle product
    const { data: product } = await useFetch(uri)

    if (!product.value) {
        throw createError({ statusCode: 404, statusMessage: 'Product not found' })
    }

    
    definePageMeta({
        layout:'products'
    })
</script>

<style scoped>

</style>