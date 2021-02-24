<template>
    <div class="hello">
        <header>
            <p>
                Calculator on Vue
            </p>
        </header>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>

    header {
        font-family: "CalculatorFont";
        margin: 0 auto;
        width: 90%;
        border: 1px lightblue dotted;

    }

</style>
