<template>
    <div class="main">
        <div class="output">
            <div class="previousOperand">{{previousOperand}}</div>
            <div class="currentOperand">{{currentOperand}}</div>
        </div>
        <button class="span-two">AC</button>
        <button>Del</button>
        <button class="operation">÷</button>
        <button @click="enterNumber(1)">1</button>
        <button @click="enterNumber(2)">2</button>
        <button @click="enterNumber(3)">3</button>
        <button class="operation">*</button>
        <button @click="enterNumber(4)">4</button>
        <button @click="enterNumber(5)">5</button>
        <button @click="enterNumber(6)">6</button>
        <button class="operation">-</button>
        <button @click="enterNumber(7)">7</button>
        <button @click="enterNumber(8)">8</button>
        <button @click="enterNumber(9)">9</button>
        <button class="operation">+</button>
        <button @click="addDecimal()">.</button>
        <button @click="enterNumber(0)">0</button>
        <button class="span-two">=</button>
    </div>
</template>

<script>
export default {
    name: 'Calculator',
    props: {

    },
    mounted: function() {
        const operationButtons = document.querySelectorAll('.operation');
        operationButtons.forEach((button) => {
            button.addEventListener('click', () => {
                this.chooseOperation(button.innerText);
            })
        })
    },
    data() {
        return {
            previousOperand: '',
            currentOperand: '',
            operation: undefined
        }
    },
    methods: {
        enterNumber (num) {
            this.currentOperand += `${num}`;
        },
        addDecimal () {
            if (this.currentOperand.includes('.')) return
            this.currentOperand += '.';
        },
        chooseOperation (operation) {
            this.operation = operation;
            this.previousOperand = this.currentOperand;
            this.currentOperand = '';
        }
    }
}
</script>

<style scoped>
    .main {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        width: 400px;
        margin: auto;
    }
    .output {
        width: 400px;
        height: auto;
        min-height: 100px;
        word-wrap: break-word;
    }
    button {
        width: 100px;
        height: 100px;
        outline: none;
    }
    .span-two {
        width: 200px;
    }
</style>