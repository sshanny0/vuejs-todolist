<template>
  <form @submit.prevent="handleSubmit">
    <input v-model="newTodo" type="text" placeholder="Tambahkan disini" maxlength="150"/>
    <button type="submit">
      <span class="text-x1 font-bold">+
      </span>
      Tambahkan Todo
    </button>
  </form>
</template>

<script setup lang="ts">
import { ref} from 'vue'

const newTodo = ref('')
const emit = defineEmits<{
  (e: 'addTodo', title: string): void
}>()

const handleSubmit = () => {
  emit('addTodo', 'Todo baru')
}
</script>
