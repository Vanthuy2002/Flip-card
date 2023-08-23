<script setup>
import { ref } from 'vue';
defineProps({
  folder: {
    type: String,
    required: true,
  },
});
const isFlip = ref(false);
const toggleFlip = () => (isFlip.value = !isFlip.value);
</script>

<template>
  <article @click="toggleFlip" class="card">
    <div :class="[isFlip ? 'flip' : '', 'card__inner']">
      <div class="card__face card__font">
        <p class="card__content"></p>
      </div>

      <div class="card__face card__back">
        <p
          class="card__content"
          :style="{
            backgroundImage: `url(${`src/assets/${folder}`})`,
          }"
        ></p>
      </div>
    </div>
  </article>
</template>
<style scoped>
.card {
  border-radius: 6px;
  width: 100px;
  height: 120px;
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
  padding: 12px;
  border-radius: 6px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.card__back {
  transform: rotateY(-180deg);
}
.card__font .card__content {
  background: url('../../assets/images/icon_back.png') no-repeat center;
  width: 100%;
  height: 100%;
  background-size: 50px;
}

.card__back .card__content {
  width: 100%;
  height: 100%;
  background-size: 40px;
  background: no-repeat center;
}
</style>
