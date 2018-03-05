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
      const re = /[1234567890-]/
      if (!re.test(event.key)) {
        event.preventDefault()
      }
    }
  },

  created () {
    this.input = this.ssn
  }
}
</script>

<style scoped>
</style>
