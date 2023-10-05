<template>
    <main class="app">
        <section class="greeting">
            <h2 class="title">
                Hey, <input type="text" placeholder="Name here" v-model="name">
            </h2>
        </section>
        <section class="create-todo">
            <h3>CREATE A TODO</h3>
            <form @submit.prevent="addTodo()">
                <h4>Whats on your todo task...</h4>
                <input type="text" class="text" placeholder="Eg. learn something new" v-model="input_content" />
                {{ input_content }}
                <h4>Pick a Category</h4>
                <div class="options">
                    <label>
                        <input type="radio" class="radio" name="category" value="professional" v-model="input_category" />
                        <span class="bubble" professional></span>
                        <div>Professional</div>
                    </label>
                    <label>
                        <input type="radio" class="radio" name="category" value="personal" v-model="input_category" />
                        <span class="bubble" personal></span>
                        <div>Personal</div>
                    </label>
                </div>
                <input type="submit" value="Add TODO" />
            </form>
        </section>
    </main>

    <!-- {{ todo_asc }} -->

    <section class="todo-list">
        <h3>TODO LIST</h3>
        <div class="list">
            <div v-for="todo in todo_asc" :class="`todo-item ${todo.done && 'done'}`">
                <label for="">
                    <input type="checkbox" name="" id="" v-model="todo.done" />
                    <span :class="`bubble ${todo.category}`"></span>
                </label>

                <div class="todo-content">
                    <input type="text" name="" id="" v-model="todo.content">
                </div>

                <div class="actions">
                    <button class="delete" v-on:click="removeTodo(todo)"> Delete </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted, computed, watch } from 'vue';

const todos = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)


const todo_asc = computed(() => todos.value.sort((a, b) => {
    return b.createdAt - a.createdAt
}))

const addTodo = () => {
    if (input_category.value.trim() === '' || input_category.value === null) {
        return
    }
    console.log('Add Todo')

    todos.value.push({
        content: input_content.value,
        category: input_category.value,
        done: false,
        createdAt: new Date().getTime()
    })
    input_content.value = ''
    input_category.value = null
}

const removeTodo = (todo) => {
    alert(1)
    console.log(todo)
    todos.value = todos.value.filter(t => t !== todo)
}

watch(todos, newval => {
    localStorage.setItem('todos', JSON.stringify(newval))
}, { deep: true })

watch(name, (newval) => {
    localStorage.setItem('name', newval)
})

onMounted(() => {
    name.value = localStorage.getItem('name') || ''
    todos.value = JSON.parse(localStorage.getItem('todos')) || []
})
</script>