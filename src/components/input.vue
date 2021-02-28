<template>
    <div class="inputBox">
        <span>
            {{mathString}}
        </span>
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
        display: flex;
        width: calc(20vw + 5px);
        height: 10vh;
        /*line-height: 10vh;*/
        padding-right: 1px;
        font-family: CalculatorFont;
        font-size: calc(3vh + 3vw);
        color: red;
        justify-content: flex-end;
        align-items: flex-end;
        border: lightblue;
        background: lightsteelblue;
    }
    span{
        /*display: flex;*/
        /*align-items: flex-end;*/
        /*justify-content: flex-end;*/
    }
</style>