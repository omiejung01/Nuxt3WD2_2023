<template>
    <div>
        <div class="py-4 ">
            <div class="flex flex-row justify-center items-center   p-1  divide divide-white ">            
                <input type="text" id="txt_username"  class="border w-40% text-base px-2 py-1 focus:outline-none focus:ring-0 focus:border-gray-800 border-gray-400" placeholder="Search" />            
            </div>
        </div>
        <div class="flex flex-col space-y-2">
            <div class="grid grid-cols-2 gap-2 ">

                <div>
                <ProductCard />
                </div>

                <div>
                <ProductCard />
                </div>

                <div>
                <ProductCard />
                </div>

                <div>
                <ProductCard />
                </div>

                
            </div>
        </div>
    </div>

</template>

<script setup lang="ts">

</script>

<style scoped>

</style>