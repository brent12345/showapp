<script setup>
import { Suspense } from 'vue';
import BreakingBadCards from './components/BreakingBadCardsSuspense.vue'
import DemonSlayer from './components/DemonSlayer.vue'
import Hero from './components/Hero.vue'
import {ref} from 'vue'

const isBreakingBad = ref(true)

</script>

<template>
 <main>
 <Hero 
 :isBreakingBad="isBreakingBad"
 @selectShow ="isBreakingBad = !isBreakingBad"
 />

    <!-- <BreakingBadCards v-if="isBreakingBad"/>
    <DemonSlayer v-else/> -->
    <KeepAlive>
    <Component :is="isBreakingBad ? BreakingBadCards : DemonSlayer" />
    </KeepAlive>  
 </main>
</template>

<style scoped>

</style>
