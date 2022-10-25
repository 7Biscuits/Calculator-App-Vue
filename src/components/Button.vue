<template>
    <button :style="{ background: color }">{{ text }}</button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            text: String,
            color: String,
        }
    }
</script>    

<style scoped>
    button {
        font-size: 35px;
        border: none;
        border-radius: 10%;
        margin-left: 5px;
        margin-bottom: 5px;
    }
</style>