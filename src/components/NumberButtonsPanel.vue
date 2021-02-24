<template>
    <div class="buttonsHolder">
        <buttons @keyDown="keyDown" class="btn" v-for="button in buttonsArray" :default-button="button" :key="button"/>
    </div>
</template>

<script>
    import Buttons from "./buttons";
    export default {
        name: "NumberButtonsPanel",
        components: {Buttons},
        data() {
            return {
                buttonsArray :
                    ["1","2","3","4",
                    "5","6","7","8",
                    "9",".","0","+/-"]
            }
        },
        methods:{
            keyDown(defaultButton){
                this.$emit("keyDown", defaultButton)
            }
        }
    }
</script>

<style scoped>
    .btn:last-child{
        font-size: calc(1vh + 1vw) !important;
        line-height:     138%;
    }
    .buttonsHolder{
        margin: 0px auto;
        height: auto;
        width: calc(15vw + 6px);
        flex-wrap: wrap;
        display: flex;
        justify-content: center;
    }
</style>