<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <hr>
  <p>Child comp - LifeCycleHooks</p>
  <LifeCycleHooks v-if="showChild" />
  <button v-on:click="showChild = !showChild">Click to Toggle Child</button>
  <h3>showChild: {{ showChild }}</h3>
  <hr>
  <TodoApp />
  <hr>
  <h2>Todo App</h2>
  <Todos />
  <hr>
  <br><br>
  <Signup />
  <hr>
  <advance character="Ram" />
  <advance character="Laxman" />
  <advance character="Sita" />
  <advance :character="character" />
  <hr>
</template>

<script>
import LifeCycleHooks from './LifeCycleHooks.vue';
import TodoApp from './TodoApp.vue';
import Todos from './Todos.vue'
import Signup from './Signup.vue'
import advance from './advance.vue';

export default {
  name: 'HelloWorld',
  components: {
    LifeCycleHooks,
    TodoApp,
    Todos,
    Signup,
    advance
  },
  data() {
    return{
      character: 'Jeet',
    }
  },
  props: {
    msg: String,
    showChild: true,
  },

  beforeCreate: function () {
    console.log('parent beforeCreate')
  },
  created() {
    console.log('parent created()')
  },
  beforeMount() {
    console.log('parent beforeMount()')
  },
  mounted() {
    console.log('parent mounted()')
  },
  beforeUpdate() {
    console.log('parent beforeUpdate()')
  },
  updated() {
    console.log('parent updated()')
  },
  beforeUnmount() {
    console.log('parent beforeUnmount()')
  },
  unmounted() {
    console.log('parent unmounted()')
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
