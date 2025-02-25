<script setup>
import TaskItem from './TaskItem.vue'
import TaskForm from './TaskForm.vue'
import { computed } from 'vue'


const props = defineProps ({
    taskItems: Array
})
const emit = defineEmits ([
  "completeTask",
  "deleteTask",
  'addTask'
])


const filteredTasks = computed(() => {
  return props.taskItems.filter((item) => !item.isComplete )
})

const tasksCount = computed(() => {
  return filteredTasks.value.length
})

const addTask = (title) => {
  emit('addTask', title)
}

const completeTask = (id) => {
  emit('completeTask', id)
}

const deleteTask = (id) => {
  emit('deleteTask', id)
}


</script>

<template>
  <div class="taskListMain">
    <TaskForm @addTask="addTask"/>
    <h2> Tasks to do - {{ tasksCount }}</h2>
    <li v-for="item in filteredTasks" :key="item.id">

    <TaskItem @completeTask="completeTask"
              @deleteTask="deleteTask"
              :title="item.title"
              :isComplete="item.isComplete"
              :id="item.id" />
    </li>
  </div>
</template>

<style scoped>

h2 {
  color: white;
}

li {
  list-style-type: none;
}

.taskListMain {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

</style>
