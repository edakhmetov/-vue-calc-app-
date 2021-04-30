<template>
    <div class="main">
        <div class="output">
            <div class="previousOperand">{{operand1}}</div>
            <div class="currentOperand"></div>
        </div>
        <button class="span-two">AC</button>
        <button>Del</button>
        <button>÷</button>
        <button @click="addNumber()">1</button>
        <button>2</button>
        <button>3</button>
        <button>*</button>
        <button>4</button>
        <button>5</button>
        <button>6</button>
        <button>-</button>
        <button>7</button>
        <button>8</button>
        <button>9</button>
        <button>+</button>
        <button>.</button>
        <button>0</button>
        <button class="span-two">=</button>
    </div>
</template>

<script>
export default {
    name: 'Calculator',
    props: {

    },
    data() {
        return {
            operand1: '',
            operand2: '',
        }
    },
    methods: {
        addNumber () {
            this.operand1 += `1`;
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