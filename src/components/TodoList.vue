<script setup lang="ts">
import { Todo } from '@/models/Todo';
import { ref } from 'vue';


const handleInput = (e: any) => { 
    todoText.value = e.target.value
;}
const addTodo = () => {
    todos.value.push(new Todo(todoText.value));
    todoText.value = "";
};
const toggleTodo = (i: number) => {
    todos.value[i].done = !todos.value[i].done;
};
const removeTodo = (i: number) => {
    todos.value.splice(i, 1);
};

const todos = ref<Todo[]>([]);
const todoText = ref("");
</script>
<template>
<main>   

<section class="container">
    <div><h1>Att göra lista</h1></div>
    <div class="inputbox">
        <input type="text" :value="todoText" @input="handleInput" @keyup.enter="addTodo"  placeholder="Skriv din Todo här"/>
        <button class="savebutton" @click="addTodo">Spara</button>
    </div>

    <ul>
        <li v-for="(todo, i) in todos" :key="todo.id">
            <span :class="todo.done ? 'done' : ''">{{ todo.text }}</span>
            <span v-if="todo.done" class="done-text"><span class="material-symbols-outlined">check</span>
</span>
            
            <div class="buttons">
                <button class="btn" @click="toggleTodo(i)">
                    {{ todo.done ? 'Ångra' : 'Klar' }}
                </button>
                <button class="btn" @click="removeTodo(i)">X</button>
            </div>
        </li>
    </ul> 
</section>
</main> 


</template>
<style scoped>

.material-symbols-outlined {
    font-size: 3.2rem;
    font-weight: bold;
    color: white;
}
main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
h1 {
    font-family:"Alfa Slab One", serif;
    font-size: 2.3rem;
    font-weight: bold;
    color: rgb(253, 86, 172);
}
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 2px solid rgb(253, 86, 172);
    width: 450px;
    border-radius: 4px;
}
.inputbox {
    display: flex;
    flex-direction: row;
    border-radius: 4px;
    justify-content: center;
    width: 416px;
    margin: 5px;
    padding: 10px;
    background-color: blueviolet;
}

input {
    border-radius: 4px;
    border: 2px solid none;
    outline: none;
    box-shadow: none;
    margin-right: 15px;
    width: 150px;
    color:blueviolet;
    font-size: 0.8rem;
    font-weight: bold;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    padding: 5px;
}
input::placeholder {
            color:blueviolet;
        }
.savebutton {
    width: 50px;
    height: 25px;
    background-color: rgb(253, 86, 172);
    border-style: none;
    color: white;
    font-weight: bold;
    text-align: center;
    border-radius: 6px;
    cursor: pointer;
    font-size: 0.8rem;
}
input:focus {
    border: 2px solid rgb(253, 86, 172);
}
.buttons {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 5px;
    width: 50px;
}
.btn {
    width: 50px;
    height: 25px;
    background-color: blueviolet;
    border-style: none;
    color: white;
    font-weight: bold;
    border-radius: 6px;
    cursor: pointer;
    font-size: 0.8rem;
}
ul {
    list-style: none;
    padding: 0;
    margin: 0;
    width: 450px;
}
li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 6px;
    gap: 6px;
    margin: 5px;
    border-radius: 5px;
    padding-left: 12px;
    color:blueviolet;
    font-weight: bold;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-size: 0.9rem;
    white-space: normal;
    word-wrap: break-word; 
    overflow-wrap: break-word;
    word-break: break-all;
}

li > .done {
    text-decoration: line-through;
}


ul li:nth-child(odd) {
  background-color: rgb(255, 157, 207);
  
}

ul li:nth-child(even) {
  background-color: rgb(199, 158, 237);
}
</style>
