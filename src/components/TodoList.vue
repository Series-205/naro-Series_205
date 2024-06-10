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
const newTaskName = ref('')

const addTask = () => {
  if (newTaskName.value != '') {
    tasks.value.push({ name: newTaskName.value, isFinished: false })
  }
}

const finishTask = (task: Task) => {
  task.isFinished = true
}
</script>

<template>
  <div>TodoList</div>
  <div>完了済</div>
  <ul>
    <li v-for="task in tasks.filter((task) => task.isFinished)" :key="task.name">
      {{ task.name }}
    </li>
  </ul>
  <div>未完</div>
  <ul>
    <li v-for="task in tasks.filter((task) => !task.isFinished)" :key="task.name">
      {{ task.name }}
      <button @click="finishTask(task)">完了</button>
    </li>
  </ul>
  <div>
    タスク名
    <input v-model="newTaskName" type="text" />
    <button @click="addTask">追加</button>
  </div>
</template>

<style></style>
