<template>
    <div class="buttonsHolder">
        <buttons @keyDown = "keyDown" class="btn" v-for="button in redactorButtons" :default-button="button" :key="button"/>
    </div>
</template>

<script>
    import Buttons from "./buttons";
    export default {
        name: "RedButtonsPannel",
        data(){
            return{
                redactorButtons : ["CE", "C", "<-"]
            }
        },
        components: {Buttons},
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
        width: calc(15vw+ 6px);
        display: flex;
        justify-content: center;
        flex-direction: row;
    }

</style>