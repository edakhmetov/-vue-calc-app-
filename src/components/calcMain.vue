<template>
    <div class="main">
        <div class="output">
            <div class="previousOperand"></div>
            <div class="currentOperand"></div>
        </div>
        <button style="span-two">AC</button>
        <button>Del</button>
        <button>÷</button>
        <button>1</button>
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
        <button style="span-two">=</button>
    </div>
</template>

<script>
export default {
    name: 'Calculator',
    props: {

    }
}
</script>

<style scoped>
    .main {
        display: flex;
        flex-direction: column;
        
    }
</style>