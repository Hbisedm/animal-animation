<script setup lang="ts">
import picsComp from '@/components/picsComp.vue'
import { ref } from 'vue'
import type { ShardComItem } from './constants/index.d'
import { staticList } from './constants'

const items = ref<ShardComItem[]>(staticList[0])
const currentLevel = ref(0)

const onChange = (newLevel: number) => {
  if (newLevel !== currentLevel.value) {
    items.value = staticList[newLevel]
    currentLevel.value = newLevel
  }
}

let scrollY = window.scrollY

window.addEventListener('scroll', () => {
  scrollY = window.scrollY
  const newSection = Math.round(scrollY / window.innerHeight)
  onChange(newSection)
})
</script>

<template>
  <div class="h-400vh bg-gradient-to-b to-#fffcdc from-#ecc0dc overflow-auto">
    <section
      v-for="(_, index) in staticList.length"
      :key="index"
      :class="`section-${index + 1}`"
    ></section>
    <div
      class="fixed bottom-0 w-40% top-50% left-50% right-0 z-8 transform translate-x--50% translate-y--50%"
    >
      <picsComp :items="items" />
    </div>
  </div>
</template>
