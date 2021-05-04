<template>
  <Calculator />
</template>

<script>
    import Calculator from './components/calcMain'

    export default {
        components: {
            Calculator
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
    }
    body {
        /* height: 100vh; */
        padding: 0;
        margin: 0;
        background: linear-gradient(0deg, rgba(150,2,111,1) 15%, rgba(0,118,255,1) 100%); 
        background-size: cover;
    }
    #app {
        height: 100vh;
        padding: 10rem
    }
</style>
