<script setup>
import { Suspense } from 'vue';
import BreakingBadCards from './BreakingBadCards.vue'
</script>

<template>
     <Suspense>
    <template #default>
        <BreakingBadCards />
    </template>
    <template #fallback>
        <div class="cards">
            <n-spin size="medium" />
        </div>
    </template>
    
 </Suspense>
</template>

<style scoped>
.cards {
    height: 700px;
    background-color: rgb(27, 26, 26);
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>