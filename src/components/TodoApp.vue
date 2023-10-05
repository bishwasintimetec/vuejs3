<template>
    <!-- <h1>TODO App</h1> -->

    <span>Create TODO</span>
    <input type="text" placeholder="type Here..." name="createTodo" v-model="createTodo" />
    <button v-on:click="getTodoData()">Create</button>
    {{ createTodo }}

    <br /><br />
    
    <input type="text" v-if="todoExist" v-model="createdTodo" ref="xyz">
    <br /><br />
    <br />
</template>

<script>
import { ref } from 'vue'

// const refvar = ref('')
export default {
    // name: 'TodoApp',
    setup() {

        const xyz = ref('')
        return {
            xyz
        }
    },
    data() {
        return {
            createTodo: null,
            createdTodo: null,
            count: 0,
            todoExist: true,
            todos: ref([])
        }
    },
    methods: {
        getTodoData() {
            this.createdTodo = this.createTodo
            this.count = this.count + 1
            alert(this.createTodo)
        }
    }
}

</script>

<style></style>