<script setup>
import TaskItem from './TaskItem.vue'
import { computed } from 'vue'

const props = defineProps ({
    taskItems: Array
})

const emit = defineEmits ([
  "returnTask"
])

const filteredTasks = computed(() => {
  return props.taskItems.filter((item) => item.isComplete )
})

const tasksDone = computed(() => {
  return filteredTasks.value.length
})

const returnTask = (id) => {
  emit('returnTask', id)
  console.log(id)
}

</script>

<template>
  <div class="taskListCompleted">
    <h2 v-show="filteredTasks.length > 0">Done - {{ tasksDone }}</h2>
    <li v-for="item in filteredTasks" :key="item.id">
      <TaskItem @returnTask="returnTask"
                :title="item.title"
                :isComplete="item.isComplete"
                :id="item.id" />

    </li>
  </div>
</template>

<style>


h2 {
  color: white;
}

li {
  list-style-type: none;
}

.taskListCompleted {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

</style>
