<template>
  <NextDialog
    v-for="(item, index) in contents"
    :key="index"
    :title="item.title"
    :isOpen="indexOpeningDialog === index"
    @next-modal="nextModal"
  >
    <img v-if="'image' in item" :src="item.image" alt="Paris" />
  </NextDialog>
  <img v-show="false" v-for="(src, index) in images" :key="index" :src="src" alt="Image" />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import NextDialog from './components/NextDialog.vue'
import paris from './assets/paris.jpg'
import firstdiving from './assets/firstdiving.jpg'

interface Content {
  title: string
  image?: string
}

const images = [paris, firstdiving]; // Preload images

const contents: Content[] = [
  {
    title: '生日快樂！'
  },
  {
    title: '這可是我嘔心瀝血做的生日禮物，你一定要喜歡喔！'
  },
  {
    title: '我們一起經歷了好多事情'
  },
  {
    title: '一起在法國旅行',
    image: paris
  },
  {
    title: '一起去小琉球潛水',
    image: firstdiving
  }
];

const indexOpeningDialog = ref(0)

function nextModal() {
  indexOpeningDialog.value += 1
}
</script>
