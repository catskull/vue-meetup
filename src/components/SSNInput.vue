<template>
  <div class="SSNInput">
    <input type="text" v-model="input">
  </div>
</template>

<script>
export default {
  name: 'SSNInput',
  data () {
    return {
      input: ''
    }
  },

  props: {
    ssn: {
      type: String,
      default: '',
      required: false
    }
  },

  methods: {

  },

  created () {
    this.input = this.ssn
  }
}
</script>

<style scoped>
</style>
