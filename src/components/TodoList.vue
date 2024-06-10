<script setup lang="ts">
import { ref } from 'vue'

interface Task {
  name: string
  isFinished: boolean
}

const tasks = ref<Task[]>([
  { name: '教科書購入', isFinished: false },
  { name: 'レポート', isFinished: false },
  { name: '環境構築', isFinished: true }
])
</script>

<template>
  <div>TodoList</div>
  <div>完了済</div>
  <ul>
    <template v-for="task in tasks" :key="task.name">
      <li v-if="task.isFinished">
        {{ task.name }}
      </li>
    </template>
  </ul>
  <div>未完</div>
  <ul>
    <template v-for="task in tasks" :key="task.name">
      <li v-if="!task.isFinished">
        {{ task.name }}
      </li>
    </template>
  </ul>
</template>

<style></style>
