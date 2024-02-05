<template>
    <div>
        <header class="shadow-sm bg-white">
            <nav class="container mx-auto p-4 flex justify-between">
                <NuxtLink to="/" class="font-bold">Online Catalog</NuxtLink>
                <ul class="flex gap-4">
                    <li>
                        <NuxtLink to="/">Home</NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/aboutus">About</NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/products" class="btn btn-blue">Products</NuxtLink>
                    </li>
                </ul>
            </nav>
        </header>

        <!-- page content go here -->
        <div class="container mx-auto p-4">
            <slot />
        </div>
    </div>
</template>

<script setup lang="ts">

</script>

<style scoped>
.router-link-exact-active {
    color: cadetblue;
}

.btn {
    @apply font-bold py-2 px-4 rounded;
}

.btn-blue {
    @apply bg-blue-500 text-white;
}

.btn-blue:hover {
    @apply bg-blue-700;
}</style>