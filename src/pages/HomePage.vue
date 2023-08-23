<script setup>
import { MainScreen, ActionScreen } from 'src/components/screen';
import { randomValues } from 'src/utils/constants';
import { ref } from 'vue';

const status = ref('default');
const settings = {
  totalBlocks: 0,
  cardContext: [],
  startedAt: null,
};

const handleBeforeStart = ({ block }) => {
  settings.totalBlocks = block;
  const firstArr = Array.from({ length: block / 2 }, (_, i) => i + 1);
  const secondsArr = [...firstArr];
  const merge = [...firstArr, ...secondsArr];
  settings.cardContext = randomValues(merge);
  settings.startedAt = new Date().getTime();

  // ready
  status.value = 'ingame';
};
</script>

<template>
  <MainScreen
    @on-start="handleBeforeStart"
    v-if="status === 'default'"
  ></MainScreen>
  <ActionScreen :block="settings.cardContext" v-if="status === 'ingame'" />
</template>

<style scoped></style>
