<script setup>
import { ref } from "vue";
const author = ref("Thuy Nguyen");
</script>
<template>
  <footer>
    <h2>This game was build with Vuejs by {{ author }}</h2>
  </footer>
</template>
<style scoped></style>
