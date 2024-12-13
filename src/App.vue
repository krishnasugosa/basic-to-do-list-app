<script setup>
import { ref } from 'vue';
const toDo = ref([]);
const newList = ref('');
const Addtodo = ()=>{
  if(newList.value.trim() !== ''){
     toDo.value.push(newList.value);
     newList.value = '';
  }
};

const deleteTodo = (index)=>{
   toDo.value.splice(index,1)
};
</script>

<template>
  <form @submit.prevent="Addtodo">
    <label for="newList" class="title">Create To Do List</label><br>
    <input type="text" id="newList" name="newList" v-model="newList" placeholder="type somethings...">
    <button class="submit-btn" type="submit">add</button>
  </form>
  <div class="wrapper-list">
    <ul>
    <li v-for="(toDos,index) of toDo">
    <span>
    <h1>Task to do <button class="deleteBtn" @click="deleteTodo(index)">X</button></h1>
    <input type="text" id="toDo" name="toDo" v-model="toDo[index]" :placeholder="toDos">
    </span>
    </li>
</ul>
  </div>
</template>

<style scoped>
.title{
  color: white;
  font-size: clamp(35px,5vw,50px);
}

form{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.wrapper-list{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

li{
  color: white;
  list-style-type: decimal;
}

span h1{
  background: linear-gradient(to top left,red,yellow);
  color: transparent;
  background-clip: text;
}

.deleteBtn{
  width: 25px;
  height: 25px;
  background-color: tomato;
  border: red;
  color: white;
  border-radius: 8px;
}
</style>
