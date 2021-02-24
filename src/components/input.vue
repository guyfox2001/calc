<template>
    <div class="inputBox">
        {{mathString}}
    </div>
</template>

<script>
    export default {
        name: "inputBox",
        props: {
            mathString:String
        }
    }
</script>

<style scoped>
    .inputBox{
        width: calc(20vw + 5px);
        height: 10vh;
        line-height: 10vh;
        vertical-align: bottom;
        padding-left: 1px;
        font-family: CalculatorFont;
        font-size: calc(3vh + 3vw);
        color: red;
        border: lightblue;
        background: lightsteelblue;
        display: flex;
        align-content: flex-end;
        justify-content: flex-end;
    }
</style>