<script setup>
import { MainScreen, ActionScreen } from "src/components/screen";
import { ref } from "vue";

const status = ref("default");

const handleBeforeStart = ({ block }) => {
  status.value = "ingame";
};
</script>

<template>
  <main-screen
    @on-start="handleBeforeStart"
    v-if="status === 'default'"
  ></main-screen>
  <ActionScreen v-if="status === 'ingame'" />
</template>

<style scoped></style>
