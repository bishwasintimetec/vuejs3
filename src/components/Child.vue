<template>
    <h1>Child Component</h1>
    <h3>Data from parent component is name : {{ name }}</h3>
    <h3>{{ user.name }}</h3>
    <button v-on:click="getData">Get parent Data</button>
</template>

<script>
export default {
    name: 'Child',
    props: {
        name: String,
        user: Object,
        getData: Function
    }
}
</script>