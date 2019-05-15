<template>
    <div class="container">
        <img src="../assets/Logo.png" />
    </div>

</template>

<script>

    export default {
        name: "Header"
    }
</script>

<style scoped>
    .container {
        width: 1fr;
        display: flex;
        justify-content: center;
        padding-right: 30px;
    }
    img {
        height: 100px;
        padding-bottom: 15px;
    }

</style>