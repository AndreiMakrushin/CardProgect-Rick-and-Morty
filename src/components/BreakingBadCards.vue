<script setup>
    import axios from "axios"
    import { ref, watch } from "vue";
    import Card from "./Card.vue"

    const characters = ref(null)
    const pages = ref(1)
    const response = await axios.get(`https://rickandmortyapi.com/api/character?page=1`);
    characters.value = response.data.results
   watch(pages, async ()=>{
    const res = await axios.get(`https://rickandmortyapi.com/api/character?page=${pages.value}`)
    characters.value = res.data.results
   })
</script>
<template>
    <div>
        <NButton strong secondary type="tertiary" @click="pages++">Next</NButton>
        <NButton strong secondary type="tertiary" @click="pages--">Prev</NButton>

        <div class="container">
            <div class="cards" v-if="characters">
                <Card
                v-for="character in characters" 
                :key="character.id" 
                :name="character.name"
                >
                <template #image>
                    <img :src="character.image">
                </template>
                </Card>
            </div>
        </div>
    </div>
</template>
<style scoped>
    /* Hero Styles */
.hero {
    height : 40vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    flex-direction: column
}
.hero img {
    position: absolute;
    height: 700px;
    opacity: 0.1;
}
.hero h1 {
    font-size: 100px;
    font-weight: bold;
}
.hero p {
    cursor: pointer;
}


/* Breaking Bad Styles */

.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: 100%
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}
.jobs {
    display: flex;
    flex-wrap: wrap;
}
.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
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

/* Rick and Morty */

.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
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
    padding-top: 30px
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}

/* Card Styles */

.n-card {
    width: 200px;
    margin:10px 20px;

}
.n-card img {
    height: 250px
}

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}
</style>