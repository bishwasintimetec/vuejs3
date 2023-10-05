<template>
    <h1>Home Component</h1>
    <h2>Create a form</h2>
    <input type="email" placeholder="enter your email" v-model="email" />
    <br /> <br />
    <input type="password" placeholder="enter your password" v-model="password" />
    <br /><br />
    <h3>Gender: </h3>
    <label for="male">Male</label>
    <input type="radio" name="gender" value="male" id="male" v-model="gender" />
    <!-- <br/><br/> -->
    <label for="female">Female</label>
    <input type="radio" name="gender" value="female" id="female" v-model="gender" />
    <br /> <br />
    <button v-on:click="getData()"> Sign In</button>


    <hr>
    <h2>Pass Data to child component</h2>
    <Child name="Bishwas Raushan" :user="user" :getData="sendData" />

    <hr><br /> <br />
    <!-- computed properties -->
    <h4>Full Name - {{ firstName }} {{ lastName }}</h4>
    <h4>With Computed First Name - {{ fullName }}</h4>

    <!-- new example -->

    <h3 v-once>Computed total - {{ total }}</h3>

    <button @click="items.push({ id: 4, title: 'Macbook', price: 4000 })">Add new Item</button>



    <hr><br /> <br />
    <h2>Watchers - volume tracker</h2>
    <h4>current volume - {{ volume }}</h4>
    <button @click="volume += 2">Increase</button>
    <button @click="volume -= 2">Decrease</button>

    <input type="text" name="movie" id="" v-model="movie">
    <input type="text" v-model="movieInfo.title">
    <input type="text" v-model="movieInfo.actor">
    <hr><br /> <br />
    <hr><br /> <br />
    <hr><br /> <br />
</template>
<script>
import Child from './Child.vue'
export default {
    name: 'HomeComp',
    // components: {
    //     Child
    // },
    data() {
        return {
            email: '',
            password: '',
            gender: null,
            user: { name: 'Bishwas', email: 'bishwas@itt.com' },
            firstName: 'Bishwas',
            lastName: 'Raushan',
            items: [
                {
                    id: 1,
                    title: 'Phone',
                    price: 1000
                },
                {
                    id: 2,
                    title: 'Tablet',
                    price: 2000
                },
                {
                    id: 3,
                    title: 'Laptop',
                    price: 3000
                }
            ],
            // watcher
            volume: 0,
            movie: 'Gadar 2',
            movieInfo: {
                title: '',
                actor: ''
            }
        }
    },
    methods: {
        getData() {
            console.log("UserData: ", this.email, this.password, this.gender)
        },
        sendData() {
            alert('Parent data called')
        }
    },
    computed: {
        fullName() {
            return `${this.firstName} ${this.lastName}`
        },
        total() {
            return this.items.reduce((total, curr) => (total += curr.price), 0)
        }
    },
    watch: {
        volume(newvalue, oldValue) {
            if (newvalue > oldValue && newvalue === 16) {
                alert('Increasing the volume can harm the hearing')
            }
            if (newvalue < 0) {
                alert('Minimum Volume reached')
            }
        },
        // movie(newValue) {
        //     console.log(`Calling API with movie name = ${newValue}`)
        // }
        movie: {
            handler(newValue) {
                console.log(`Calling API with movie name = ${newValue}`)
            },
            immediate: true
        },
        movieInfo: {
            handler(newValue) {
                console.log(`Movie title is ${newValue.title} and actor is ${newValue.actor}`)
            },
            deep: true          // handler won't work with nested data so need to use deep in place of immediate
        }


    }
}
</script>
<style scoped>
h1 {
    color: orange
}
</style>