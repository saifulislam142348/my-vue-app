<script setup>
import { ref ,reactive} from 'vue'


const count = ref(0)
const color = ref('none')
const people=reactive(
{
    name:'saiful',
    age:20,
    job:'Software Enginner',
}
);
</script>

<template>
    <section class="mx-auto container">
        <h1 class="text-2xl mb-10">Vue Form</h1>
        <p class="pb-5">Your Favorite Color:{{ color }}</p>
        <p>
            <label for="">Value </label>
            <input type="text" class="w-32 " placeholder="Enter The value" v-model="color">
        </p>
    </section> 
     <section class="mx-auto container">
        <h1 class="text-2xl mb-10">Vue Object using V-model</h1>
        
        <div class="flex flex-col md5 text-left" v-for="(value,key) in people" :key="key">
            <label for="\">{{ key }}</label>
            <input type="text" class="border border-spacing-1 border-gray-400  rounded-md p-2 " placeholder="Enter The value" v-model="people[key]" readonly>
        </div>
    </section>
    <section class="mx-auto container">
        <h1 class="text-2xl mb-10">Person Information</h1>
        
        <div class="flex flex-col md5 text-left" v-for="(value,key) in people" :key="key">
            <label for="\">{{ key }}</label>
            <input type="text" class="border border-spacing-1 border-gray-400  rounded-md p-2 " placeholder="Enter The value" v-model="people[key]" >
        </div>
    </section>
</template>

<style scoped></style>