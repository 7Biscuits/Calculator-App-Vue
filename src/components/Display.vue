<template>
    <div class="display">
        <div class="num">{{ number }}</div>
    </div>
</template>

<script>
    export default {
        name: 'Display',
        props: {
            number: String
        },
    }
</script>

<style scoped>
    .display {
        width: 20rem;
        height: 5.4rem;
        margin: auto;
        text-align: right;
        font-size: 2.5em;
        border-radius: 5px;
        color: rgb(49, 126, 207);
    }
    .num {
        padding: 20px;
    }
</style>