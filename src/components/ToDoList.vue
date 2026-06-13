<!-- src/components/ItemList.vue -->
<script setup lang="ts">
import { ref } from 'vue'

interface ToDoList {
  name: string
  isCompleted: boolean
}

const items = ref<ToDoList[]>([
  { name: '物理課題', isCompleted: false },
  { name: 'ゴミ出し', isCompleted: false },
])
const newItemName = ref('')


const addItem = () => {
  if (items.value.some((item) => item.name === newItemName.value)) return
  items.value.push({ name: newItemName.value, isCompleted: false })
}

const completeTask = (name: string) => {
  items.value.forEach((item) =>{
    if( item.name == name){
        item.isCompleted = true
    }
  })
}
</script>

<template>
  <div>
    <div>ToDo</div>
    <ul>
      <li v-for="item in items.filter((item) => !item.isCompleted)" :key="item.name" >
        <div>{{ item.name }}</div>
        <button @click="completeTask(item.name)">完了</button>
      </li>
    </ul>
    <div>Done</div>
    <ul>
      <li v-for="item in items.filter((item) => item.isCompleted)" :key="item.name" >
        <div>{{ item.name }}</div>
      </li>
    </ul>
    <div>
      <label>
        新しいタスク
        <input v-model="newItemName" type="text" />
      </label>
      <button @click="addItem">追加</button>
    </div>
  </div>
</template>

