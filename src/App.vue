<script setup>
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'
import axios from 'axios'
import { onMounted, reactive, ref, watch } from 'vue'
const items = ref([])
const favorites = ref([])
const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})
const fetchFavorites = async () => {
  const { data: favorites } = await axios
    .get('https://604781a0efa572c1.mokky.dev/favorites', {})
    .catch(console.error)
  favorites.value = favorites
  items.value = items.value.map((item) => {
    const favorite = favorites.value.find((favorite) => favorite.itemId === item.id)

    if (!favorite) {
      return item
    }
    return {
      ...item,
      isFavorite: true,
      favoriteId: favorite.id
    }
  })
}
const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}
const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
}
const pickQueries = (queries) => {
  const dictQuery = {
    sortBy: 'sortBy',
    searchQuery: 'title'
  }
  return queries.reduce((queryObj, el) => {
    if (filters[el]) {
      const currentKey = dictQuery[el]
      if (currentKey === 'title') {
        queryObj[currentKey] = `*${filters[el]}*`
      } else {
        queryObj[currentKey] = filters[el]
      }
    }
    return queryObj
  }, {})
}

const addToFavorite = async (item) => {
  item.isFavorite = true
}

const fetchItems = async () => {
  const params = pickQueries(Object.keys(filters))
  const { data } = await axios
    .get('https://604781a0efa572c1.mokky.dev/items', {
      params
    })
    .catch(console.error)
  items.value = data.map((item) => ({ ...item, isFavorite: false, isAdded: false }))
}
onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})
watch(filters, fetchItems)
</script>
<template>
  <!-- <Drawer /> -->
  <div class="w-4/5 mx-auto bg-white rounded-xl shadow-xl mt-14">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center mb-8">
        <h2 class="text-3xl font-bold">All Sneakers</h2>
        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-2 px-3 border rounded-md outline-none"
            name=""
            id=""
          >
            <option value="name">by name</option>
            <option value="price">ascending price</option>
            <option value="-price">descending price</option>
          </select>
          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="search" />
            <input
              class="border rounded-md py-2 pl-11 pr-4 outline-none"
              type="text"
              @change="onChangeSearchInput"
              placeholder="Search..."
            />
          </div>
        </div>
      </div>
      <CardList :items="items" :addToFavorite="addToFavorite" />
    </div>
  </div>
</template>
<style scoped></style>
