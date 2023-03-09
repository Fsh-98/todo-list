<template>
    <div>
        <div>
            {{ todo.title }}
        </div>
        <button @click="$emit('delete', i)">Delete</button>
        <button @click="$emit('editTodo', i)">Edit</button>
    </div>
</template>

<script>
export default {
    props: {
        todo: Object,
        isEdit: Boolean,
        editableTodo: Number,
        todos: Array
    },

    methods: {

    }
}
</script>