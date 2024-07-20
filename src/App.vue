<script setup>
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'

const items = [
  {
    id: 1,
    title: 'Мужские Кроссовки Nike Blazer Mid Suede',
    price: 12999,
    imageUrl: '/sneakers/sneakers-1.jpg'
  },
  {
    id: 2,
    title: 'Мужские Кроссовки Nike Air Max 270',
    price: 15600,
    imageUrl: '/sneakers/sneakers-2.jpg'
  },
  {
    id: 3,
    title: 'Мужские Кроссовки Nike Blazer Mid Suede',
    price: 8499,
    imageUrl: '/sneakers/sneakers-3.jpg'
  },
  {
    id: 4,
    title: 'Кроссовки Puma X Aka Boku Future Rider',
    price: 7800,
    imageUrl: '/sneakers/sneakers-4.jpg'
  },
  {
    id: 5,
    title: 'Кроссовки Future Rider',
    price: 9550,
    imageUrl: '/sneakers/sneakers-5.jpg'
  },
  {
    id: 6,
    title: 'Кроссовки Black Edition',
    price: 16999,
    imageUrl: '/sneakers/sneakers-6.jpg'
  },
  {
    id: 7,
    title: 'Кроссовки Orange Boomb Edition',
    price: 7499,
    imageUrl: '/sneakers/sneakers-7.jpg'
  },
  {
    id: 8,
    title: 'Кроссовки Nike Air Max 270',
    price: 15600,
    imageUrl: '/sneakers/sneakers-8.jpg'
  }
]
</script>
<template>
  <!-- <Drawer /> -->
  <div class="w-4/5 mx-auto bg-white rounded-xl shadow-xl mt-14">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center mb-8">
        <h2 class="text-3xl font-bold">All Sneakers</h2>
        <div class="flex gap-4">
          <select class="py-2 px-3 border rounded-md outline-none" name="" id="">
            <option value="by name">by name</option>
            <option value="asc by price">ascending price</option>
            <option value="desc by price">descending price</option>
          </select>
          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="search" />
            <input
              class="border rounded-md py-2 pl-11 pr-4 outline-none"
              type="text"
              placeholder="Search..."
            />
          </div>
        </div>
      </div>
      <CardList :items="items" />
    </div>
  </div>
</template>
<style scoped></style>
