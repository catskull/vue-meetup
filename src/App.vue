<template>
  <div id="app">
    <h1>Parent social is: {{ssn}}</h1>
    <ssn-input v-model="ssn"></ssn-input>
  </div>
</template>

<script>
import SSNInput from './components/SSNInput'

export default {
  name: 'App',

  components: {
    'ssn-input': SSNInput
  },

  data () {
    return {
      ssn: ''
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
