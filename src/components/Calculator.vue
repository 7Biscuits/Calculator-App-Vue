<template>
  <div class="calculator">
    <Display :number="number" />
    <Buttons @displayUpdate="updateDisplay" />
  </div>
</template>

<script>
import Display from './Display.vue'
import Buttons from './Buttons.vue'

export default {
  name: 'Calculator',
  components: {
    Display,
    Buttons,
  },
  data() {
    return {
      number: ''
    }
  },
  methods: {
    updateDisplay(num) {
      this.number = num
    }
  }
}
</script>

<style scoped>
  .calculator {
    display: inline-block;
    background-color: #2c3e50;;
    padding: 50px;
    border-radius: 15px;
  }
</style>