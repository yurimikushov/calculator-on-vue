<template>
  <div className="calculator">
    <screen :previewResult="previewResult" :result="enteredValues"></screen>
    <num-pad
      :showEnteredValue="showEnteredValue"
      :showResult="showResult"
      :deleteLastEnteredValue="deleteLastEnteredValue"
      :clearEnteredValues="clearEnteredValues"
    ></num-pad>
  </div>
</template>

<script>
import Screen from './../Screen.vue'
import NumPad from './../NumPad.vue'
import {
  isNumber,
  isSeparator,
  isMathOperator,
  isAssignmentOperator,
  isDeleteOperator,
  isClearOperator,
} from './input-validator'
import { MATH_OPERATOR, SERVISE_OPERATOR, ERROR_RESULT } from './../../constants'

export default {
  name: 'Calculator',
  components: {
    screen: Screen,
    'num-pad': NumPad,
  },
  data() {
    return {
      previewResult: '',
      enteredValues: '',
    }
  },
  methods: {
    showEnteredValue: function (enteredValue) {
      const updatedEnteredValues =
        this.enteredValues !== ERROR_RESULT
          ? this.enteredValues.concat(enteredValue)
          : '' + action.enteredValue

      this.previewResult = this.calcPreviewResult(updatedEnteredValues)
      this.enteredValues = updatedEnteredValues
    },
    showResult: function () {
      this.previewResult = ''
      this.enteredValues = this.calcResult(this.enteredValues)
    },
    deleteLastEnteredValue: function () {
      const updatedEnteredValues =
        this.enteredValues !== ERROR_RESULT
          ? this.enteredValues.substring(0, this.enteredValues.length - 1)
          : ''

      this.previewResult = this.calcPreviewResult(updatedEnteredValues)
      this.enteredValues = updatedEnteredValues
    },
    clearEnteredValues: function () {
      this.previewResult = ''
      this.enteredValues = ''
    },
    calcPreviewResult: function (enteredValues) {
      const lastEnteredValue = enteredValues[enteredValues.length - 1]

      return !isMathOperator(lastEnteredValue) ? this.calcResult(enteredValues) : ''
    },
    calcResult: function (enteredValues) {
      try {
        return '' + (eval(fixEnteredValues(enteredValues)) || '')
      } catch (e) {
        return ERROR_RESULT
      }

      function fixEnteredValues(values) {
        return values
          .replaceAll(MATH_OPERATOR.MULTIPLICATION, MATH_OPERATOR.AlT_MULTIPLICATION)
          .replaceAll(MATH_OPERATOR.DIVISION, MATH_OPERATOR.AlT_DIVISION)
      }
    },
  },
}
</script>

<style>
.calculator {
  position: absolute;
  top: 50%;
  left: 50%;
  background-color: var(--calc-bg-color);
  box-shadow: 0 0 20px 5px #00000024;
  transform: translate(-50%, -50%);
}
</style>
