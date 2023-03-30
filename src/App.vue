<script setup>
  import Unic from './components/Unic.vue';
  import Hero from './components/Hero.vue';
  import CardsSuspense from './components/CardsSuspense.vue';
  import {ref} from "vue"


  const isBreakingBad = ref(true)
</script>
<template>
  <div>
    <Hero :isBreakingBad="isBreakingBad" @selectShow="isBreakingBad = !isBreakingBad"/>
    <!-- <CardsSuspense v-if="isBreakingBad"/>
    <Unic v-else/> -->
    <KeepAlive>
      <Component :is="isBreakingBad ? CardsSuspense : Unic"/>
    </KeepAlive>
  </div>
  </template>
  <style scoped>
    .cards{
      height: 700px;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  </style>