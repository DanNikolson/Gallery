<script setup>
defineProps({
  id: Number,
  previewURL: String,
  largeImageURL: String,
  likes: Number,
  views: Number
})

const openModal = (largeImageURL) => {
  window.dispatchEvent(new CustomEvent('openModal', { detail: { largeImageURL } }))
}
</script>

<template>
  <div
    class="relative bg-white border border-slate-100 w-full h-48 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl"
    @click="openModal(largeImageURL)"
  >
    <img :src="previewURL" class="h-3/4 w-full" alt="Science" />
    <div class="grid grid-cols-1 grid-rows-2 mt-1 relative">
      <div class="flex gap-3 items-center">
        <img src="/public/likes.svg" class="w-[1.5rem] h-[1.5rem]" alt="Like" />
        <b>{{ likes }}</b>
      </div>
      <div class="flex gap-3 items-center">
        <img src="/public/views.svg" class="w-[1.5rem] h-[1.5rem]" alt="Views" />
        <b>{{ views }}</b>
      </div>
    </div>
  </div>
</template>
