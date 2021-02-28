<template>
    <HelloWorld/>
    <div class="calc">
        <div class="inputPanel">
            <div class="calcMemory">{{calcMem}}</div>
            <input-box :math-string="getCalcRes"/>
        </div>
        <div class="allButtons">
            <div class="calcNumbers">
                <red-buttons-pannel @keyDown="keyDown"/>
                <number-buttons-panel @keyDown="keyDown"/>
            </div>
            <div class="calcActions">
                <MathButtonsPanel @keyDown="keyDown"/>
            </div>
        </div>
    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld.vue'
    import NumberButtonsPanel from "./components/NumberButtonsPanel";
    import RedButtonsPannel from "./components/RedButtonsPannel";
    import MathButtonsPanel from "./components/MathButtonsPanel";
    import InputBox from "./components/input";

    export default {
        name: 'App',
        data() {
            return {
                leastPressedBtn: '*',
                calcMem: 0,
                calcRes: "0",
                flagCh: false
            }
        },
        components: {
            InputBox,
            MathButtonsPanel,
            RedButtonsPannel,
            NumberButtonsPanel,
            HelloWorld
        },
        computed: {
            getCalcRes() {
                return this.calcRes;
            }
        },
        methods: {
            keyDown(defaultButton) {
                console.log(defaultButton);
                switch (defaultButton) {
                    default: {
                        if (this.flagCh == true){
                            this.calcRes ='0'
                            this.flagCh = false
                        }
                        if (this.calcRes !=='0') {
                            this.calcRes += defaultButton

                        }
                        else {
                                this.calcRes = defaultButton
                        }
                        break;
                    }

                    case ".": {
                        if (!this.calcRes.includes(".")) {
                            this.calcRes += '.'
                        }
                        break;
                    }
                    case "-": {
                        this.leastPressedBtn ='-'
                        if (this.calcMem === 0){
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = '0'
                        }
                        break;
                    }
                    case "+": {
                        this.leastPressedBtn ='+'
                        if (this.calcMem === 0){
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = '0'
                        }
                        break;
                    }
                    case "*": {
                        this.leastPressedBtn ='*'
                        if (this.calcMem === 0){
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = '0'
                        }
                        break;
                    }
                    case "/": {
                        this.leastPressedBtn ='/'
                        if (this.calcMem === 0){
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = '0'
                        }
                        break;
                    }
                    case "=": {
                        switch (this.leastPressedBtn) {
                            case "-": {
                                this.calcRes = (this.calcMem - parseFloat(this.calcRes)).toString()
                                console.log(this.calcRes);
                                console.log(this.calcMem);
                                break;
                            }
                            case "+": {
                                this.calcRes = (this.calcMem + parseFloat(this.calcRes)).toString()
                                break;
                            }
                            case "*": {
                                this.calcRes = (this.calcMem * parseFloat(this.calcRes)).toString()
                                break;
                            }
                            case "/": {
                                this.calcRes = (this.calcMem / parseFloat(this.calcRes)).toString()
                                break;
                            }
                        }
                        this.calcMem = 0
                        console.log(this.calcMem)
                        this.flagCh = true
                        break;
                    }
                    case "CE": {
                        this.calcRes = "0"
                        break;
                    }
                    case "C": {
                        this.calcRes = "0"
                        this.calcMem = 0
                        this.leastPressedBtn = "*"
                        break;
                    }
                    case "<-": {
                        if (this.calcRes.length === 1) {
                            this.calcRes = '0';
                        } else {
                            this.calcRes = this.calcRes.slice(0, this.calcRes.length - 1);
                        }
                        break;
                    }
                    case "+/-": {
                        if (this.calcRes.includes("-")) {
                            this.calcRes = this.calcRes.replace("-", '');
                            console.log(true);
                        } else {
                            if (this.calcRes !== "0") {
                                this.calcRes = "-" + this.calcRes;
                            }
                        }
                        break;
                    }

                }
            }
        }
    }
</script>

<style>
    body {
        display: flex;
        background: #2c3e50;
    }

    @font-face {
        font-family: CalculatorFont;
        src: url("./fonts/Digital7-1e1Z.ttf");
    }

    .calcMemory{
        position: absolute;
        top: 0; left: 0;
    }
    .calcNumbers {
        margin: 0px;
        justify-content: flex-end;
        display: flex;
        flex-direction: column;
    }

    .calcActions {
        margin: 0px;
        justify-content: flex-start;
        display: flex;
        flex-direction: column;

    }

    .allButtons {
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: center;
    }

    .inputPanel {
        /*width: 20vw;*/
        position: relative;
        display: flex;
        justify-content: center;
    }

    .calc {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    #app {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 100%;
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: lightblue;
        margin-top: 60px;
    }
</style>
