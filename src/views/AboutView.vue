<script setup>
import { ref } from 'vue'

const menu = ref([
  { id: 1, name: '珍珠奶茶', description: '香濃奶茶搭配QQ珍珠', price: 50, stock: 20 },
  { id: 2, name: '冬瓜檸檬', description: '清新冬瓜配上新鮮檸檬', price: 45, stock: 18 },
  { id: 3, name: '翡翠檸檬', description: '綠茶與檸檬的完美結合', price: 55, stock: 34 },
  { id: 4, name: '四季春茶', description: '香醇四季春茶，回甘無比', price: 45, stock: 10 },
  { id: 5, name: '阿薩姆奶茶', description: '阿薩姆紅茶搭配香醇鮮奶', price: 50, stock: 25 },
  { id: 6, name: '檸檬冰茶', description: '檸檬與冰茶的清新組合', price: 45, stock: 20 },
  { id: 7, name: '芒果綠茶', description: '芒果與綠茶的獨特風味', price: 55, stock: 18 },
  { id: 8, name: '抹茶拿鐵', description: '抹茶與鮮奶的絕配', price: 60, stock: 20 },
])

const updateItem = (item) => {
  console.log('更新項目:', item)
}

const decreaseStock = (item) => {
  if (item.stock > 0) {
    item.stock--
    updateItem(item)
  }
}

const increaseStock = (item) => {
  item.stock++
  updateItem(item)
}
</script>

<template>
  <div class="container mx-auto p-4">
    <table class="w-full border-collapse border border-gray-300">
      <thead>
        <tr class="bg-gray-100">
          <th class="border border-gray-300 p-2">品項</th>
          <th class="border border-gray-300 p-2">描述</th>
          <th class="border border-gray-300 p-2">價格</th>
          <th class="border border-gray-300 p-2">庫存</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in menu" :key="item.id" class="border-b border-gray-300">
          <td class="border border-gray-300 p-2">
            <input v-model="item.name" class="w-full" @blur="updateItem(item)">
          </td>
          <td class="border border-gray-300 p-2"><small>{{ item.description }}</small></td>
          <td class="border border-gray-300 p-2">{{ item.price }}</td>
          <td class="border border-gray-300 p-2 flex items-center justify-between">
            <button @click="decreaseStock(item)" class="bg-red-500 text-white px-2 py-1 rounded">-</button>
            <input v-model.number="item.stock" type="number" class="w-16 text-center" @blur="updateItem(item)">
            <button @click="increaseStock(item)" class="bg-green-500 text-white px-2 py-1 rounded">+</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>