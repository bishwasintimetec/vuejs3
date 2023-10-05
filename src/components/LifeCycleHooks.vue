<template>
    <h1>Life Cycle Hooks component</h1>
</template>

<script>
export default {

    name: 'LifeCycleHooks',
    data() {
        return {}
    },
    methods: {},

    beforeCreate: function () {
        console.log('child beforeCreate')
    },
    created() {
        console.log('child created()')
    },
    beforeMount() {
        console.log('child beforeMount()')
    },
    mounted() {
        console.log('child mounted()')
    },
    beforeUpdate() {
        console.log('child beforeUpdate()')
    },
    updated() {
        console.log('child updated()')
    },
    beforeUnmount() {
        console.log('child beforeUnmount()')
    },
    unmounted() {
        console.log('child unmounted()')
    }

}
</script>