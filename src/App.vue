<script setup>
import TaskList from './views/TaskList.vue'
import TaskListCompleted from './views/TaskListCompleted.vue'
import { ref } from 'vue'

const taskItems = ref([])

const addTask = (title) => {
  taskItems.value.push({
    id: Date.now(),
    title: title,
    isComplete: false,
  })
}

const completeTask = (id) => {
  const currentItem = taskItems.value.find((item) => item.id == id)
  currentItem.isComplete = true
}

const deleteTask = (id) => {
  taskItems.value = taskItems.value.filter((item) => item.id !== id)
}

const returnTask = (id) => {
  const currentItem = taskItems.value.find((item) => item.id == id)
  currentItem.isComplete = false
}
</script>

<template>
  <div class="main">
    <TaskList
      @add-task="addTask"
      @complete-task="completeTask"
      @delete-task="deleteTask"
      :taskItems="taskItems"
    />
    <TaskListCompleted @return-task="returnTask" :task-items="taskItems" />
  </div>
</template>

<style scoped>
.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  margin-left: auto;
  margin-right: auto;
  padding-top: 20px;
}
</style>
