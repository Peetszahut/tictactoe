<template>
    <div class="container">
        <form @submit.prevent="loginSubmit">
            <label for="username-login">Enter Username:</label>
            <input type="text" v-model="username" id="username-login">

            <label for="password-login">Enter Password</label>
            <input type="password" v-model="password" id="password-login">

            <button class="btn-submit" @click="goHome">Sign in as Guest</button>
            <input type="submit" value="Submit" class="btn-submit" @click="goHome">
        </form>
    </div>
</template>

<script>
    export default {
        name: "Login",
        data() {
            return {
                username: '',
                password: ''
            }
        },
        methods: {
            loginSubmit() {
                console.log(this.username);
                console.log(this.password);
                this.username = '';
                this.password = '';
            },
            goHome() {
                this.$emit('goHome', 'game')
            }
        }
    }

</script>

<style scoped>
    label {
        font-family: Georgia,sans-serif;
        margin-bottom: 10px;
    }
    input {
        margin-bottom: 10px;
    }

    .btn-submit {
        font-family: Georgia,sans-serif;
        background-color: #016CFF;
        border: none;
        color: white;
        padding-top: .5rem;
        padding-bottom: .5rem;
        text-align: center;
        text-decoration: none;
        font-size: 14px;
        border-radius: 8px;
        box-shadow: 1px 1px #404040;
        margin-bottom: .5rem;
    }
    .container{
        display: flex;
        width:1fr;
        justify-content: center;
    }
    form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 300px;
    }
</style>