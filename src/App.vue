<template>
  <NextDialog
    v-for="(item, index) in contents"
    :key="index"
    :title="item.title"
    :isOpen="indexOpeningDialog === index"
    @next-modal="nextModal"
  >
    <img v-if="'image' in item" :src="item.image" alt="Paris" />
    <p v-else v-for="(line, lineIndex) in item.content.split('\n')" :key="lineIndex">{{ line }}</p>
  </NextDialog>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import NextDialog from './components/NextDialog.vue'

interface ImageContent {
  title: string
  image: string
}

interface TextContent {
  title: string
  content: string
}

const contents: (ImageContent | TextContent)[] = [
  {
    title: '生日快樂！',
    content: ''
  },
  {
    title: '這可是我嘔心瀝血做的生日禮物，你一定要喜歡喔！',
    content: ''
  },
  {
    title: '我們一起經歷了好多事情',
    content: '',
  },
  {
    title: '一起在法國旅行',
    image: '/cynthia-birthday/src/assets/paris.jpg'
  },
  {
    title: '一起在法國旅行2',
    content: 'haha'
  }
]

const indexOpeningDialog = ref(0)

function nextModal() {
  indexOpeningDialog.value += 1
}
</script>
