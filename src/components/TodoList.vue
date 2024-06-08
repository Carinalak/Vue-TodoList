<script setup lang="ts">
import { ref } from 'vue';


const addTodo = () => {
    todo.value.push(new Todo(todoText.value));
}

const todos = ref<Todo[]>([]);
const todoText = ref("");
const handleInput = (e: any) => { 
    todoText.value = e.target.value
;}




</script>

<template>
 

 <div>
<input type="text" :value="todoText" @input="handleInput"/>
<button @click="addTodo">Spara</button>

 </div>


</template>








<style scoped>

</style>
