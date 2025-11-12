<template>
  <div class="max-w-[600px] my-8 mx-auto px-4">
    <TodoForm @add-todo="addNewTodo"/>
    <ul class="bg-white/80 backdrop-blur-md rounded-2x1 p-6 shadow-lg">
      <li v-for="(item, key) in sortedList" :key="key">
        <Task :isChecked="item.checked" @change="updateItem(item)">
          {{ item.title }}
        </Task>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import Task from './TaskItem.vue'
import { ref, computed, type Ref, onMounted } from 'vue' // ref itu untuk reactive data, dia akan mengubah nilai data secara otomatis di template, pada kasus ini untuk checked
import TodoForm from './TodoForm.vue'

type Item = {
  title: string
  checked: boolean
}

const storageItems: Ref<Item[]> = ref([])

const getFromStorage = () => {
  const stored = localStorage.getItem('todo-list')

  if (stored) {
    return JSON.parse(stored)
  }
  return[]
}

const setToStorage = (items: Item[]): void => {
  localStorage.setItem('todo-list', JSON.stringify(items))
}

const initListItems = (): void => {
  if (storageItems.value?.length === 0 ) {
    const listitems: Item[] = [
      { title: "Instalasi Vue.js", checked: true },
      { title: "Membuat Todo List App!", checked: false },
      { title: "Menambahkan fungsi Todo", checked: false },
      { title: "Mengedit fungsi Todo", checked: false },
      { title: "Menghapus fungsi Todo", checked: false },
      { title: "Push ke repositori github", checked: false },
      { title: "Publikasikan Hasilnya!", checked: false },
  ]
  setToStorage(listitems)
  storageItems.value = listitems
  }
}

const updateItem = (item: Item): void => {
  const updatedItem = findItemInList(item)
  if (updatedItem) {
      toggleItemChecked(updatedItem)
      setToStorage(storageItems.value)
  }
}

// membandingkan value
const findItemInList = (item: Item): Item | undefined => {
  return storageItems.value.find((itemInList: Item) => itemInList.title === item.title)
}

// merubah status checklist
const toggleItemChecked = (item: Item): void => {
  item.checked = !item.checked
}

// sort unchecked list paling atas
const sortedList = computed(() => {
  return [...storageItems.value].sort((a, b) => (a.checked ? 1 : 0) - (b.checked ? 1 : 0))
})

const addNewTodo = (title: string): void => {
  const newItem: Item = {
    title,
    checked: false,
  }
  storageItems.value.unshift(newItem)
  setToStorage(storageItems.value)
}
onMounted(() => {
  storageItems.value = getFromStorage()
  initListItems()
}
)
</script>
