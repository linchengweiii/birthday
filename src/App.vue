<template>
  <NextDialog
    v-for="(item, index) in contents"
    :key="index"
    :title="item.title"
    :is-open="indexOpeningDialog === index"
    @next-modal="nextModal"
  >
    <img v-if="'image' in item" :src="item.image" alt="Paris" />
  </NextDialog>
  <SelectionDialog
    :title="lastTitle"
    :is-open="indexOpeningDialog === contents.length"
    @cancel-modal="doubleConfirm"
    @close-modal="nextModal"
  />
  <DoubleConfirmDialog
    :title="doubleConfirmTitle"
    :is-open="isDoubleConfirm"
    @close-modal="isDoubleConfirm = false"
  />
  <div class="h-screen flex flex-col justify-center bg-blue-100">
    <img v-if="indexOpeningDialog > contents.length && !isDoubleConfirm" :src="happyBirthday" />
  </div>
  <img v-show="false" v-for="(src, index) in images" :key="index" :src="src" alt="preload-image" />
</template>

<script setup lang="ts">
import { ref } from 'vue'

import paris from './assets/paris.jpg'
import firstdiving from './assets/firstdiving.jpg'
import taipeiSunset from './assets/taipei-sunset.jpg'
import taitung from './assets/taitung.jpg'
import newYear from './assets/new-year.jpg'
import tainan from './assets/tainan.jpg'
import valentine from './assets/valentine.jpg'
import diving from './assets/diving.jpg'

import heart1 from './assets/heart1.jpg'
import heart2 from './assets/heart2.jpg'
import heart3 from './assets/heart3.jpg'
import heart4 from './assets/heart4.jpg'
import heart5 from './assets/heart5.jpg'
import heart6 from './assets/heart6.jpg'

import happyBirthday from './assets/happy-birthday.png'

import NextDialog from './components/NextDialog.vue'
import SelectionDialog from './components/SelectionDialog.vue'
import DoubleConfirmDialog from './components/DoubleConfirmDialog.vue'

interface Content {
  title: string
  image?: string
}

// Preload images
const images = [
  paris,
  firstdiving,
  taipeiSunset,
  taitung,
  newYear,
  tainan,
  diving,
  heart1,
  heart2,
  heart3,
  heart4,
  heart5,
  heart6
]

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
    image: taitung
  },
  {
    title: '一起跨年',
    image: newYear
  },
  {
    title: '一起去台南玩',
    image: tainan
  },
  {
    title: '一起過情人節',
    image: valentine
  },
  {
    title: '又一起去小琉球潛水',
    image: diving
  },
  {
    title: '經過了好多個日日夜夜'
  },
  {
    title: '',
    image: heart1
  },
  {
    title: '',
    image: heart2
  },
  {
    title: '',
    image: heart3
  },
  {
    title: '',
    image: heart4
  },
  {
    title: '',
    image: heart5
  },
  {
    title: '',
    image: heart6
  },
  {
    title: '我們一起經歷了好多事情'
  },
  {
    title: '希望你的 20 歲順順利利、快快樂樂'
  },
  {
    title: '繼續跟我吵吵鬧鬧'
  }
]

const lastTitle = '我們一起繼續探索這個世界好嗎？'

const doubleConfirmTitle = '我們一起繼續探索這個世界好嗎(怒)？'

const indexOpeningDialog = ref(0)

const isDoubleConfirm = ref(false)

function nextModal() {
  indexOpeningDialog.value += 1
}

function doubleConfirm() {
  indexOpeningDialog.value += 1
  isDoubleConfirm.value = true
}
</script>
