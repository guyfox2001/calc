<template>
    <div class="buttonsHolder">
        <buttons @keyDown = "keyDown" class="btn" v-for="button in mathButtons" :default-button="button" :key="button"/>
    </div>
</template>

<script>
    import Buttons from "./buttons";
    export default {
        name: "MathButtonsPanel",
        components: {Buttons},
        data(){
            return {
                mathButtons: ["-","+","*","/","="]
            }
        },
        methods:{
            keyDown(defaultButton) {
                return this.$emit('keyDown', defaultButton)
            }
        }
    }
</script>

<style scoped>
    .buttonsHolder{
        margin: 0px auto;
        height: auto;
        width: calc(5vw + 2px);
        flex-wrap: wrap;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
    }
</style>