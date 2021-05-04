<template>
    <div class="main">
        <div class="output">
            <div class="previous-operand">{{previousOperand}} {{operation}}</div>
            <div class="current-operand">{{currentOperand}}</div>
        </div>
        <button class="span-two" @click="clear()">AC</button>
        <button @click="deleteNumber()">DEL</button>
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
        <button @click="compute()" class="span-two equals">=</button>
    </div>
</template>

<script>
export default {
    name: 'Calculator',
    mounted: function() {
        const operationButtons = document.querySelectorAll('.operation');
        operationButtons.forEach((button) => {
            button.addEventListener('click', () => {
                this.chooseOperation(button.innerText);
            })
        });
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
        deleteNumber () {
            this.currentOperand = this.currentOperand.toString().slice(0, -1);
        },
        addDecimal () {
            if (this.currentOperand.includes('.')) return
            this.currentOperand += '.';
        },
        chooseOperation (operation) {
            if (this.currentOperand === '') return
            if (this.previousOperand !== '') {
                this.compute();
            }
            this.operation = operation;
            this.previousOperand = this.currentOperand;
            this.currentOperand = '';
        },
        compute () {
            let computation;
            const prev = parseFloat(this.previousOperand);
            const current = parseFloat(this.currentOperand);
            if (isNaN(prev) || isNaN(current)) return
            switch (this.operation) {
                case '+':
                    computation = prev + current
                    break
                case '-':
                    computation = prev - current
                    break
                case '*':
                    computation = prev * current
                    break
                case '÷':
                    computation = prev / current
                    break
                default:
                    return
            }
            this.currentOperand = computation.toString();
            this.operation = undefined;
            this.previousOperand = '';
        },
        clear () {
            this.currentOperand = '';
            this.previousOperand = '';
            this.operation = undefined;
        }
    }
}
</script>

<style scoped>
    .main {
        display: flex;
        flex-wrap: wrap;
        width: 400px;
        margin: auto;
    }
    .output {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: flex-end;
        width: 400px;
        max-height: auto;
        background-color: rgba(0, 0, 0, 0.6);
        min-height: 120px;
        word-wrap: break-word;
        word-break: break-all;
        padding: 10px;
    }
    button {
        width: 100px;
        height: 100px;
        font-size: 2rem;
        border: 1px solid white;
        cursor: pointer;
        outline: none;
        background-color: rgba(255, 255, 255, .6);
    }
    button:hover {
        background-color: rgba(255, 255, 255, .9);
    }
    .span-two {
        width: 200px;
    }
    .output .previous-operand {
        color: rgba(255, 255, 255, 0.75);
        font-size: 1rem;
    }
    .output .current-operand {
        color: white;
        font-size: 2rem;
    }
</style>