<template>
  <div class="SSNInput">
    <input
      type="text"
      v-model="input"
      @keydown="preventInput"
    >
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
    preventInput () {
      let allowModifiers = false
      let charMatch = /[1234567890-]/
      if (event.ctrlKey || event.metaKey) {
        charMatch = /[xvca]/
        allowModifiers = true
      }
      const keyMatch = /(Backspace|Tab)/

      if (!keyMatch.test(event.key) && !charMatch.test(event.key)) {
        event.preventDefault()
      } else if (!allowModifiers && charMatch.test(event.key) && this.input.length >= 11) {
        event.preventDefault()
      }
    },

    format () {

    }
  },

  created () {
    this.input = this.ssn
  }
}
</script>

<style scoped>
</style>
