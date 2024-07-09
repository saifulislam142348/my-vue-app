<script setup>
import { ref, reactive } from 'vue'


const countries =reactive( [
    {
        name: 'Bangladesh',
        capital: 'Dhaka',
    }, {
        name: 'Afghanistan',
        capital: 'Kabul',
    },
    {
        name: 'Albania',
        capital: 'Tirana (Tirane)',
    },
    {
        name: 'Algeria',
        capital: 'Algiers ',
    }]);
const capitals = ["Dhaka", "Kabul", "Tirana (Tirane)", "Algiers"];
//  function  capitalRandom(){
//    return capitals.sort(()=>Math.random()-0.5);
// }
function getScore(){
    let score=0;
    countries.forEach(country=> {
        if(country.capital===country.answer){
            score++
        }
       

    });
    return score;
}
</script>
<template>
    <section>
        <h1>Quiz System in Vue js </h1>
        <p>{{ countries }}</p>
        <h2 class="p-5">Count Score: {{getScore()}}</h2>
        <div class="box-border h-20 w-90 p-4 border-4" v-for="country in countries" :key="country.name">
            <p>Where is the capital of {{ country.name }}? </p>
            <template  v-for="capital in capitals" :key="capital">
                <input class="p-4" type="radio" :name="country.name" :value="capital" v-model="country.answer" />
                <label  class="p-4">{{ capital }}</label>
            </template>



        </div>
    </section>
</template>
<style scoped></style>