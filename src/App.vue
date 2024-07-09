<template>
  <ParisDialog :isOpen="indexOpeningDialog === 0" @next-modal="nextModal"/>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import ParisDialog from './components/ParisDialog.vue'

const indexOpeningDialog = ref(0);

function nextModal() {
  indexOpeningDialog.value += 1;
}
</script>
