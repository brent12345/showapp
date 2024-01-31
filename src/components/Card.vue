<script setup>
    // import { defineProps } from 'vue';

    const {image, name, title } = defineProps(['image', 'name', 'lastname','title' ])
    
</script>

<template>

  <n-card>
    <template #cover>
      <img :src="image">
    </template>
   <h3>{{ name }} {{ lastname }}</h3>
   <p>{{ title }}</p>
   <slot></slot>
  </n-card>

</template>


<style scoped>
.n-card {
    width: 200px;
    margin:10px 20px;

}
.n-card img {
    height: 250px
}

</style>