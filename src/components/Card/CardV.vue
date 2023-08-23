<script setup>
import { ref } from 'vue';

const isFlip = ref(false);

const toggleFlip = () => (isFlip.value = !isFlip.value);
</script>
<template>
  <article @click="toggleFlip" class="card">
    <div :class="[isFlip ? 'flip' : '', 'card__inner']">
      <div class="card__face card__font">
        <p class="card__content">Font</p>
      </div>

      <div class="card__face card__back">
        <p class="card__content">Back</p>
      </div>
    </div>
  </article>
</template>
<style scoped>
.card {
  border-radius: 6px;
  width: 120px;
  height: 90px;
}
.card__inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.25s linear;
  transform-style: preserve-3d;
  cursor: pointer;
}
.flip {
  transform: rotateY(-180deg);
}
.card__face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  overflow: hidden;
  border-radius: 6px;
  padding: 16px;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
}
.card__back {
  background-color: coral;
  transform: rotateY(-180deg);
}
</style>
