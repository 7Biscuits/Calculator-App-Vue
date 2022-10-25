<template>
    <div class="buttons">
        <Button @click="clear()" :text="'C'" :color="'#41B883'" style="color: white" />
        <Button @click="del()" :text="'Del'" :color="'#41B883'" style="color: white" />
        <Button @click="percentage()" :text="'%'" :color="'#41B883'" style="color: white" />
        <Button @click="multiply()" :text="'x'" :color="'#41B883'" style="color: white" />
        <Button @click="append('7')" :text="'7'" />
        <Button @click="append('8')"  :text="'8'" />
        <Button @click="append('9')"  :text="'9'" />
        <Button @click="divide()" :text="'÷'" :color="'#41B883'" style="color: white" />
        <Button @click="append('4')" :text="'4'" />
        <Button @click="append('5')" :text="'5'" />
        <Button @click="append('6')" :text="'6'" />
        <Button @click="substract()" :text="'-'" :color="'#41B883'" style="color: white" />
        <Button @click="append('3')" :text="'3'" />
        <Button @click="append('2')" :text="'2'" />
        <Button @click="append('1')" :text="'1'" />
        <Button @click="add()" :text="'+'" :color="'#41B883'" style="color: white" />
        <Button @click="equal()" :text="'='" :color="'#41B883'" style="color: white" />
        <Button @click="append('0')" :text="'0'" />
        <Button @click="decimal()" :text="'.'" />
    </div>
    
</template>

<script>
import Button from './Button.vue'

    export default {
        name: 'Buttons',
        components: {
            Button,
        },
        data() {
            return {
                currentNumber: '',
                previousNumber: '',
                operator: null
            }
        },  
        methods: {
            updateDisplay() {
                this.$emit('displayUpdate', this.currentNumber)
            },
            append(number) {
                if (this.currentNumber.length < 10) {
                    this.currentNumber = `${this.currentNumber}${number}`
                    this.updateDisplay()
                } 
            },
            clear() {
                this.currentNumber = '',
                this.updateDisplay()
            },
            del() {
                this.currentNumber = this.currentNumber.slice(0, this.currentNumber.length - 1)
                this.updateDisplay()
            },
            decimal() {
                if (this.currentNumber.indexOf('.') === -1) this.append('.')
            },
            setPrevious() {
                this.previousNumber = this.currentNumber
                this.currentNumber = ''
            },
            add() {
                this.setPrevious()
                this.operator = (a, b) => a + b
                this.updateDisplay()
            },
            substract() {
                this.setPrevious()
                this.operator = (a, b) => a - b
                this.updateDisplay()
            },  
            multiply() {
                this.setPrevious()
                this.operator = (a, b) => a * b
                this.updateDisplay()
            },  
            divide() {
                this.setPrevious()
                this.operator = (a, b) => a / b
                this.updateDisplay()
            },
            percentage() {
                this.setPrevious()
                this.operator = (a, b) => (b / a) * 100
                this.updateDisplay()
            },
            equal() {
                this.currentNumber = this.operator(
                    parseFloat(this.previousNumber), parseFloat(this.currentNumber) 
                )
                this.previousNumber = ''
                this.updateDisplay()
            },
        },
    }
</script>

<style scoped>
    .buttons {
        margin: 20px auto;
        width: 320px;
        display: grid;
        background-color: #2c3e50;
        grid-template-columns: repeat(4, 1fr);
        grid-auto-rows: minmax(77px, auto);
    }
    .buttons button:hover {
        cursor: pointer;
        background-color: #3e5165;
    }
</style>