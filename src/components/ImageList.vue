<script setup>
import Image from './Image.vue'

defineProps({
  items: Array
})
</script>

<template>
  <div class="grid grid-cols-auto-fill-150 mx-4 gap-8">
    <Image
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :previewURL="item.previewURL"
      :largeImageURL="item.largeImageURL"
      :likes="item.likes"
      :views="item.views"
    />
  </div>
</template>
