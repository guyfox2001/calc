<template>
    <button @click="$emit('keyDown', defaultButton)">
        {{defaultButton}}
    </button>
</template>

<script>
    export default {
        name: 'buttons',
        props: {
            defaultButton: String
        }
    }
</script>


<style scoped>
    button {
        height: 5vh;
        width: 5vw;
        margin: 1px;
        font-family: CalculatorFont;
        font-size: calc(1vh + 1vw);
        border: 1px lightblue solid;
        background: lightsteelblue;
    }

    button:active {
        background: aqua;
        outline: none;
    }

    button:focus {
        outline: none;
        box-shadow: none;
    }
</style>
