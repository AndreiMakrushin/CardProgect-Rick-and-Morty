<script setup>
    import {defineProps} from "vue"

    const { name } = defineProps([ 'name'])
</script>
<template>
    <NCard>
        <template #cover>
            <slot name="image"></slot>
           <!--  <img :src="image"> -->
        </template>
        <h2>{{ name }}</h2>
        <slot></slot>
  </NCard>
</template>
<style scoped>
.n-card {
    width: 200px;
    margin:10px 20px;
    height: 100%;
}
.n-card img {
    height: 250px
}
</style>