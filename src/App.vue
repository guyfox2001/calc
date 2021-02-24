<template>
    <HelloWorld/>
    <div class="calc">
        <div class="inputPanel">
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
                calcRes: "0"
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
                    case "0": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '0'
                        }
                        break;
                    }
                    case "1": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '1'
                        } else {
                            this.calcRes = "1"
                        }
                        break;
                    }
                    case "2": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '2'
                        } else {
                            this.calcRes = "2"
                        }
                        break;
                    }
                    case "3": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '3'
                        } else {
                            this.calcRes = "3"
                        }
                        break;
                    }
                    case "4": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '4'
                        } else {
                            this.calcRes = "4"
                        }
                        break;
                    }
                    case "5": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '5'
                        } else {
                            this.calcRes = "5"
                        }
                        break;
                    }
                    case "6": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '6'
                        } else {
                            this.calcRes = "6"
                        }
                        break;
                    }
                    case "7": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '7'
                        } else {
                            this.calcRes = "7"
                        }
                        break;
                    }
                    case "8": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '8'
                        } else {
                            this.calcRes = "8"
                        }
                        break;
                    }
                    case "9": {
                        if (this.calcRes !== "0") {
                            this.calcRes += '9'
                        } else {
                            this.calcRes = "9"
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
                        this.leastPressedBtn = '-'
                        if (this.calcMem !== 0) {
                            this.calcRes = (this.calcMem - parseFloat(this.calcRes)).toString()
                        } else {
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = "0"
                        }
                        break;
                    }
                    case "+": {
                        this.leastPressedBtn = '+'
                        if (this.calcMem !== 0) {
                            this.calcRes = (this.calcMem + parseFloat(this.calcRes)).toString()
                        } else {
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = "0"
                        }
                        break;
                    }
                    case "*": {
                        this.leastPressedBtn = '*'
                        if (this.calcMem !== 0) {
                            this.calcRes = (this.calcMem * parseFloat(this.calcRes)).toString()
                        } else {
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = "0"
                        }
                        break;
                    }
                    case "/": {
                        this.leastPressedBtn = '/'
                        if (this.calcMem !== 0) {
                            this.calcRes = (this.calcMem / parseFloat(this.calcRes)).toString()
                        } else {
                            this.calcMem = parseFloat(this.calcRes)
                            this.calcRes = "0"
                        }
                        break;
                    }
                    case "=": {
                        switch (this.leastPressedBtn) {
                            case "-": {
                                this.calcRes = (this.calcMem - parseFloat(this.calcRes)).toString()
                                console.log(this.calcRes);
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
