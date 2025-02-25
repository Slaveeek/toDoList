<script setup>
import { ref } from 'vue';

const inputText = ref("")

</script>


<template>
  <!-- сюда добавить addTask, v-model для textЮ чтобы передавать введенное название task -->
  <div  class="header">
    <input type="text" v-model="inputText" class="input" placeholder="Add a new task" />
    <button @click="$emit('addTask', inputText)" type="button" class="button"><img src="../assets/plus-icon.png" alt=""></button>
  </div>
</template> 

<style scoped>

.header {
  display: flex;
}

.input {
  width: 375px;
  height: 40px;
  margin-right: 10px;
  border: 1px solid #3E1671;
  background: none;
  padding-left: 14px;
  color: #9E78CF;
  box-sizing: border-box;
}

.input::placeholder {
  color: white;
}

.button {
  background-color: #9E78CF;
  /* background: url(..assets/plus-icon.png) center no-repeat; */
  color: #FFFFFF;
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 10px;
}

/* .input {
  opacity: 0%;
} */

</style>
