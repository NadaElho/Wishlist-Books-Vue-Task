<script>
    export default{
        data:()=>({
            user:{
                name: '',
                password: ''
            },
            submit: false
        }),
        methods: {
            goToShopping(){
                this.$emit("submitted")
               
            }
        },
    }
</script>

<template>
 <h3 class="text-light" v-if="!submit">Register</h3>
 <h3 class="text-light" v-else>User Data</h3>
<div class="d-flex flex-column gap-2 w-50 mx-auto" v-if="!submit">
    <input type="text" v-model="user.name" placeholder="name">
    <input type="password" v-model="user.password" placeholder="password">
    <button class="btn btn-success" :disabled="!user.name || !user.password" @click="submit=true">Next</button>
</div>
<div v-else>
    <div>Username: {{ user.name }}</div>
    <div>Password: {{ user.password }}</div>
    <button class="btn btn-success" @click="submit=false">Back</button>
    <button class="btn btn-success ms-2" @click="goToShopping()">Submit</button>
</div>
</template>

<style>

</style>
