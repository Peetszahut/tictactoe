<template>
    <div class="container">
        <p>Welcome to the Registration</p>
        <div>
            <form @submit.prevent="loginSubmit">
                <label for="username">Choose a Username:</label>
                <input type="text" v-model="username" id="username">

                <label for="password">Choose a Password:</label>
                <input type="password" v-model="password" id="password">

                <label for="passwordReEnter">Re-Enter Password:</label>
                <input type="password" v-model="passwordReEnter" id="passwordReEnter">

                <input type="submit" value="Create Account" class="btn-submit">
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Register",
        data() {
            return {
                username: '',
                password: '',
                passwordReEnter: ''
            }
        },
        methods: {
            createAccount () {

            }
        }
    }
</script>

<style scoped>
    .container {
        display: flex;
        width: 600px;
        justify-content: center;
        flex-direction: column;
        font-family: Georgia, sans-serif;
    }

    form {
        display: flex;
        flex-direction: column;
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
</style>