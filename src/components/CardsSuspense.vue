<script setup>
import BreakingBadCards from './BreakingBadCards.vue'
</script>
<template>
    <Suspense>
      <template #default> 
        <BreakingBadCards/>
      </template>
      <template #fallback>
        <div class="cards spinner">
          <n-spin size="large" />
        </div>
      </template>
    </Suspense>
</template>