<script setup>
import Card from './Card.vue'
defineProps({
  items: Array,
  addToFavorite: Function
})
const onClickAdd = () => {
  alert(111)
}
const onClickFavorite = () => {}
</script>
<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :isFavorite="item.isFavorite"
      :onClickAdd="onClickAdd"
      :onClickFavorite="addToFavorite"
    />
  </div>
</template>
