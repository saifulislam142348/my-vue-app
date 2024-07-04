<script setup>
import { ref } from 'vue'

const arrayData=ref([]);
</script>

<template>
   
    
    <section class="mx-auto container">
        <h1 class="text-2xl mb-10">Check box using array data include</h1>
        
        <div class="flex flex-col md5 text-left">
            <label for="\">{{ arrayData }}</label>
            <label for="\">Red</label>
            <input type="checkbox" class="border border-spacing-1 border-gray-400  rounded-md p-2 " value="red" v-model="arrayData" >
            <label for="\">Green</label>
            <input type="checkbox" class="border border-spacing-1 border-gray-400  rounded-md p-2 " value="green" v-model="arrayData" >
        </div>
    </section>
</template>

<style scoped></style>