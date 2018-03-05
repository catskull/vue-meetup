<template>
  <div id="ssn-input">
    <input
      type="text"
      placeholder="Social Security Number"
      v-model="social"
      @keydown="preventChar"
      @keyup="disableCopy"
      @paste="parsePaste"
      maxlength="11"
    >
    <h3>Component social is: {{social}}</h3>
  </div>
</template>

<script>
export default {
  name: 'ssn-input',
  data () {
    return {
      social: '',
      allowedKeys: ['Backspace', 'Tab', 'Control', 'Meta', 'ArrowLeft', 'ArrowRight', 'Left', 'Right'],
      copyEnabled: false
    }
  },

  props: {
    value: {
      type: String,
      default: '',
      required: false
    }
  },

  methods: {
    preventChar (event) {
      if (event.key === 'Control' || event.key === 'Meta') {
        this.copyEnabled = true
      }

      if (!'0123456789'.includes(event.key) &&
          !this.allowedKeys.includes(event.key) &&
          !('acvx'.includes(event.key) && this.copyEnabled)) {
        event.preventDefault()
      }
    },
    disableCopy (event) {
      if (event.key === 'Control' || event.key === 'Meta') {
        this.copyEnabled = false
      }
    },
    parsePaste (event) {
      const clipboardData = event.clipboardData || window.clipboardData
      const pastedData = clipboardData.getData('Text').replace(/[^0-9.]/g, '').substring(0, 9)
      event.preventDefault()
      const tempNum = this.social + pastedData
      this.social = tempNum.substr(0, 11)
    }
  },

  watch: {
    social (val, oldVal) {
      let num = val.replace(/\D/g, '')
      if (num.length > 5) {
        num = `${num.slice(0, 3)}-${num.slice(3, 5)}-${num.slice(5)}`
      } else if (num.length > 3) {
        num = `${num.slice(0, 3)}-${num.slice(3)}`
      }
      this.social = num
      this.$emit('input', this.social)
    }
  },

  created () {
    this.social = this.value
  }
}
</script>

<style scoped>
  input {
    font-size: 30px;
  }
</style>
