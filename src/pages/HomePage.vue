<script setup>
import { MainScreen, ActionScreen } from "src/components/screen";
import { ref } from "vue";

const status = ref("default");

const handleBeforeStart = ({ block }) => {
  status.value = "ingame";
};
</script>

<template>
  <MainScreen
    @on-start="handleBeforeStart"
    v-if="status === 'default'"
  ></MainScreen>
  <ActionScreen v-if="status === 'ingame'" />
</template>

<style scoped></style>
