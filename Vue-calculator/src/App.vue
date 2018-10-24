<template>

  <div id="app">

    <h1>Calculator</h1>
     <Calculator/>
   
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'app',
  components: {
    Calculator
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Raleway');
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}



html, body{
  height: 100%;
  margin: 0;
  padding: 0;
  background-repeat: no-repeat;
  overflow: auto;
  text-align: center;
  background-attachment: fixed;
  background: repeating-linear-gradient(-45deg, #901d8c, #de3452, #e3901d);

}

h1{
  margin: 0;
  font-family: 'Raleway', sans-serif;
  letter-spacing: 12px;
  text-transform: uppercase;
  padding: 30px;
  color: #fff;
}

</style>
