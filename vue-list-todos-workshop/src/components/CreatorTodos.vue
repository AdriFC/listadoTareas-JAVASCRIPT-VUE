import { default } from '../App.vue';
<template>
    <div>
    <input 
        v-model="nameTodo"
        type="text">
    <button @click="addTodo"> Añadir tarea </button>
    </div>
</template>

<script>
export default {
    name: 'CreatorTodos',
    data() {
        return {
            nameTodo: ''
        }
    },
    methods: {
        addTodo() {
            this.$emit('add-todo', this.nameTodo)
        }
    }
}
</script>

