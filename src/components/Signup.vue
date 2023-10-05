<template>
    <h3>Sign up Form</h3>

    <form class="signup" @submit="submitForm">
        <div>
            <label for="name">Name</label>
            <input type="text" name="name" id="name" v-model="formValues.name">
        </div>

        <div>
            <label for="profile">Profile Summary</label>
            <textarea id="profile" v-model="formValues.profileSummary" />
        </div>

        <div>
            <label for="country">Country</label>
            <select id="country" v-model="formValues.country">
                <option value="">Select a Country</option>
                <option value="india"> India</option>
                <option value="nepal"> Nepal</option>
                <option value="bhutan"> Bhutan</option>
            </select>
        </div>
        <div>
            <label for="job-location">Job Location</label>
            <select id="job-location" multiple v-model="formValues['job-location']">
                <option value="india"> India</option>
                <option value="nepal"> Nepal</option>
                <option value="bhutan"> Bhutan</option>
            </select>
        </div>
        <div>
            <input type="checkbox" name="" id="remoteWork" v-model="formValues.remoteWork" true-value="yes"
                false-value="no">
            <label for="remoteWork">Open to remote work?</label>
        </div>

        <div>
            <label for="">Skill Set</label>
            <input type="checkbox" id="html" value="html" v-model="formValues.skillSet">
            <label for="html">HTML</label>
            <input type="checkbox" id="css" value="css" v-model="formValues.skillSet">
            <label for="css">CSS</label>
            <input type="checkbox" id="javascript" value="javascript" v-model="formValues.skillSet">
            <label for="javascript">JavaScript</label>
        </div>

        <div>
            <label for="age">Age</label>
            <input @keyup.enter="submitForm" type="number" name="age" id="age" v-model="formValues.age">
        </div>

        <!-- <div>
            <button>Submit</button>
        </div> -->

    </form>


    <div>
        <pre>
            {{ JSON.stringify(formValues, 0, 2) }}
        </pre>
    </div>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.3.1/dist/css/bootstrap.min.css"
        integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    <!-- <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous">
    </script> -->
    <!-- <script src="https://cdn.jsdelivr.net/npm/popper.js@1.14.7/dist/umd/popper.min.js"
        integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous">
    </script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.3.1/dist/js/bootstrap.min.js"
        integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous">
    </script> -->
</template>

<script>
export default {
    name: 'Signup',
    data() {
        return {
            formValues: {
                name: '',
                profileSummary: '',
                country: '',
                'job-location': [],
                remoteWork: false,
                skillSet: [],
                age: null
            }
        }
    },
    methods: {
        submitForm(event) {
            event.preventDefault()
            console.log('Form Values', this.formValues)
        }
    }
}


</script>

<style>
/* 
#div {
    width: 22rem;
    padding: 10px 10px 10px 10px;
    border: 1px solid darkgrey;
    background: whitesmoke;
    text-align: center;
} */
</style>