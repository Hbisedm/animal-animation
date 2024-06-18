<template>
  <div className="relative w-full h-full min-w-20">
    <div v-for="(item, index) in items" className="absolute w-full h-full" :key="index">
      <div
        className="w-full h-full transition-all duration-1000 ease-in-out"
        :style="{
          backgroundColor: item.color,
          clipPath: `polygon(${item.polygon})`,
          transitionDelay: `${index * 15}ms`
        }"
      ></div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  items: {
    type: Array<any>
  }
})
</script>
