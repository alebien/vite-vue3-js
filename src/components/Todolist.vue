<template>
    <div>
        <input type="text" v-model="title" @keyup.enter="addTodos">
        <ul v-if="todos.length">
            <li v-for="(todo, index) in todos" :key="index">
                <input type="checkbox" v-model="todo.done">
                <span :class="{ done: todo.done }">{{todo.title}}</span>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref } from "vue";
let title = ref("");
let todos = ref([{ title: '学习Vue', done: false }]);
function addTodos() {
    todos.value.push({
        title: title.value,
        done: false,
    });
    title.value = '';
}
</script>
<style scoped>
.done {
    color: grey;
    text-decoration: line-through;
}
</style>