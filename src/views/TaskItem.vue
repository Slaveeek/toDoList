<script setup>
// import { ref } from 'vue'
defineProps({
  id: Number,
  title: String,
  isComplete: Boolean
});



</script>

<template>
  <div class="taskItem">
    <h3 :class="{'completedTaskTitle': isComplete, 'newTaskTitle': !isComplete}" >{{ title }}</h3>
    <div class="buttons">
      <!-- v-if на кнопки, по свойству isComplete скрываем у задач, которые выполнены -->
      <button v-show="!isComplete" @click="$emit('completeTask', id)" class="checkButton"></button>
      <button v-show="!isComplete" @click="$emit('deleteTask', id)" class="deleteButton"></button>
      <button v-show="isComplete" @click="$emit('returnTask', id)" class="returnTaskButton"> CANCEL </button>
    </div>
  </div>
</template>

<style scoped>
.taskItem {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #15101c;
  width: 432px;
  height: 75px;
  border-radius: 10px;
  gap: 10px;
}

.newTaskTitle {
  color: #9e78cf;
  padding-left: 20px;
}

.completedTaskTitle {
  color: #78CFB0;
  padding-left: 20px;
}

.buttons {
  display: flex;
  justify-content: space-between;
  gap: 8px;
  width: 68px;
  align-content: center;
  margin-right: 20px;
}

.checkButton {
  background: url(../assets/checkMarkIcon.png) center no-repeat;
  border: none;
  width: 30px;
  height: 30px;
  padding: 0;
  /* background: none; */
}

.deleteButton {
  background: url(../assets/trashIcon.png) center no-repeat;
  border: none;
  width: 30px;
  height: 30px;
  padding: 0;
}

.returnTaskButton {
  background-color: #15101c;
  color: white;
}

</style>
