<script setup>
import { CardFlip } from 'src/components/Card';
import { ref } from 'vue';
defineProps({
  block: {
    type: Array,
    default: () => [],
  },
});

const images = ref('images');
</script>
<template>
  <section class="flex">
    <CardFlip
      v-for="(card, index) in block"
      :key="index"
      :folder="`${images}/${card}.png`"
      :index="index + 1"
    />
  </section>
</template>
<style scoped>
.flex {
  max-width: 768px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px;
  margin: 30px auto;
}
</style>
