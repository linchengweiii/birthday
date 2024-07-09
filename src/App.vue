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
import taipeiSunset from './assets/taipei-sunset.jpg'
import taitung from './assets/taitung.jpg'
import newYear from './assets/new-year.jpg'
import tainan from './assets/tainan.jpg'
import diving from './assets/diving.jpg'

interface Content {
  title: string
  image?: string
}

const images = [paris, firstdiving, taipeiSunset, taitung, newYear, tainan, diving]; // Preload images

const contents: Content[] = [
  {
    title: '寶寶 20 歲生日快樂！'
  },
  {
    title: '這可是我嘔心瀝血做的生日小驚喜，你一定要喜歡喔！'
  },
  {
    title: '在一起快要一年了'
  },
  {
    title: '我們一起經歷了好多事情'
  },
  {
    title: '一起在法國旅行',
    image: paris
  },
  {
    title: '一起去潛水',
    image: firstdiving
  },
  {
    title: '一起在台北看夕陽',
    image: taipeiSunset
  },
  {
    title: '一起去台東玩',
    image: taitung,
  },
  {
    title: '一起跨年',
    image: newYear
  },
  {
    title: '一起去台南玩',
    image: tainan,
  },
  {
    title: '又一起去小琉球潛水',
    image: diving
  },
];

const indexOpeningDialog = ref(0)

function nextModal() {
  indexOpeningDialog.value += 1
}
</script>
