<script setup>
import { modeGame } from 'src/utils/constants';

defineEmits(['on-start']);
</script>

<template>
  <section>
    <h1>Pokemon Flip Card</h1>
    <h3>Select mode to begin game</h3>
    <div class="grid">
      <button
        v-for="mod in modeGame"
        :key="mod.id"
        @click="$emit('on-start', { block: mod.block })"
      >
        <span>{{ mod.mode }}</span>
        <span>{{ mod.options }}</span>
      </button>
    </div>
  </section>
</template>

<style scoped></style>
