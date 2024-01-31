<script setup>
import { ref, computed } from "vue";
import axios from "axios";
import Card from "./Card.vue"
 
const characters = ref([]);
const currentPage = ref(1);
const charactersPerPage = 8;
 
const response = await axios.get("https://thronesapi.com/api/v2/characters");
characters.value = response.data;


const paginatedCharacters = computed(() => {
  const startIndex = (currentPage.value - 1) * charactersPerPage;
  const endIndex = startIndex + charactersPerPage;
  return characters.value.slice(startIndex, endIndex);
});
 
const nextPage = () => {
  if (
    currentPage.value < Math.ceil(characters.value.length / charactersPerPage)
  ) {
    currentPage.value++;
  }
};
 
const previousPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
};

   
</script>

<template>
    <div class="container">
        <div class="cards">
            <Card 
            v-for="character in paginatedCharacters" 
            :key="character.id"
            :image="character.imageUrl" 
            :name="character.firstName" 
            :lastname="character.lastName" 
            :title="character.title">
                <!-- <div class="jobs">
                    <p v-for="(job, index) in occupation" :key="job">
                        {{ job }}<span v-if="index < occupation.length - 1">,&nbsp</span>
                    </p>
                    <h1>Hello Slot</h1>
                </div>  -->
            </Card>
      <div class="button-container">
        <button @click="previousPage">&lt</button>
        <button @click="nextPage">></button>
      </div>
      </div>
    </div>
  </template>

<style scoped>
.container {
    background-color: rgb(27, 26, 26);
    padding: 30px;
    height: inherit;
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: inherit;
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}

.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px;
    width: 100%;
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}
.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}


</style>