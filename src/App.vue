<script setup lang="ts">
import LeftBanner from './components/LeftBanner.vue'
import TestFile from './components/TestFile.vue'
</script>

<template>
  <div class="_container flex justify-between">
    <div class="flex-none h-full md:w-60 w-20">
      <LeftBanner />
    </div>
    <div class="flex-none h-full w-16 bg-red-400"></div>
    <div class="flex-grow h-full">
      <TestFile />
    </div>
  </div>
</template>

<style scoped></style>
