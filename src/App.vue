<template>
  <div id="app">
    <ssn-input :ssn="ssn"></ssn-input>
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
      ssn: '123'
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
