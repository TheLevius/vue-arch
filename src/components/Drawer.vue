<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
</script>
<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="flex flex-col bg-white w-96 h-full fixed right-0 top-0 p-10 z-20">
    <DrawerHead />
    <CartItemList />
    <div class="flex flex-col gap-4 mt-auto">
      <div class="flex gap-2">
        <span>Total: </span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>$180</b>
      </div>
      <div class="flex gap-2">
        <span>Tax: </span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>$30</b>
      </div>
      <button
        disabled="false"
        class="bg-lime-500 w-full rounded-xl mt-8 py-3 text-white hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-400 transition cursor-pointer"
      >
        checkout order
      </button>
    </div>
  </div>
</template>
