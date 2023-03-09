<template>
    <div>
        <h1>This is a to-do list</h1>
        <ul>
            <li v-for="(todo, i) in todos" :key="i">
                <TodoItem :todo="todo" @emitDelete="deleteTodo(i)" @emitEdit="editTodo(i)"/>
            </li>
        </ul>
        <form v-if="!isEdit" @submit.prevent="addTodo">
            <input type="text" v-model="newTodo">
            <button type="submit">Add</button>
        </form>
        <form v-else @submit.prevent="updateTodo">
            <input type="text" v-model="newTodo">
            <button type="submit">Update</button>
        </form>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
const STORAGE_KEY = 'todo-app-key'
export default {
    components: {
        TodoItem
    },
    created() {
        this.todos = JSON.parse(localStorage.getItem(STORAGE_KEY));
    },
    data() {
        return {
            newTodo: "",
            isEdit: false,
            editableTodo: null,
            todos: []
        };
    },
    methods: {
        addTodo() {
            this.todos.push({ title: this.newTodo });
            localStorage.setItem(STORAGE_KEY, JSON.stringify(this.todos));
            this.newTodo = "";
        },
        updateTodo() {
            this.todos[this.editableTodo].title = this.newTodo;
            this.newTodo = "";
            this.isEdit = false;
        },
        deleteTodo(index) {
            this.todos.splice(index, 1);
            localStorage.setItem(STORAGE_KEY, JSON.stringify(this.todos));
        },
        editTodo(index) {
            this.isEdit = true;
            this.editableTodo = index;
            this.newTodo = this.todos[this.editableTodo].title;
        },
    },
}
</script>
