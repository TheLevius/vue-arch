<script setup>
defineProps({
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
})
</script>
<template>
  <div
    class="relative border border-slate-100 rounded-3xl p-8 bg-white cursor-pointer hover:-translate-y-2 hover:shadow-xl transition"
  >
    <img
      :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
      :alt="isFavorite ? 'Liked' : 'Like'"
      :onClickAdd="onClickAdd"
      class="absolute top-8 left-8"
      @click="onClickFavorite"
    />
    <img :src="imageUrl" alt="sneakers" />
    <p class="mt-2">{{ title }}</p>
    <div class="flex justify-between mt-5">
      <div class="flex justify-col">
        <span class="text-slate-400">price:</span>
        <b>${{ price }}</b>
      </div>
      <img :src="isAdded ? '/checked.svg' : '/plus.svg'" alt="Plus" @click="onClickAdd" />
    </div>
  </div>
</template>
