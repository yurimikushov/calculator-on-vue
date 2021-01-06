<template>
  <div class="number-pad">
    <div class="number-pad__line">
      <top-operator
        :title="SERVISE_OPERATOR.CLEAR"
        :onClick="clearEnteredValues"
      ></top-operator>
      <top-operator
        :title="MATH_OPERATOR.OPENING_PARENTHESIS"
        :onClick="showEnteredValue"
      ></top-operator>
      <top-operator
        :title="MATH_OPERATOR.CLOSING_PARENTHESIS"
        :onClick="showEnteredValue"
      ></top-operator>
      <top-operator
        :title="SERVISE_OPERATOR.DELETE"
        :onClick="deleteLastEnteredValue"
      ></top-operator>
    </div>
    <div class="number-pad__line">
      <number :title="7" :onClick="showEnteredValue"></number>
      <number :title="8" :onClick="showEnteredValue"></number>
      <number :title="9" :onClick="showEnteredValue"></number>
      <right-side-operator
        :title="MATH_OPERATOR.DIVISION"
        :onClick="showEnteredValue"
      ></right-side-operator>
    </div>
    <div class="number-pad__line">
      <number :title="4" :onClick="showEnteredValue"></number>
      <number :title="5" :onClick="showEnteredValue"></number>
      <number :title="6" :onClick="showEnteredValue"></number>
      <right-side-operator
        :title="MATH_OPERATOR.SUBSRTACTION"
        :onClick="showEnteredValue"
      ></right-side-operator>
    </div>
    <div class="number-pad__line">
      <number :title="1" :onClick="showEnteredValue"></number>
      <number :title="2" :onClick="showEnteredValue"></number>
      <number :title="3" :onClick="showEnteredValue"></number>
      <right-side-operator
        :title="MATH_OPERATOR.MULTIPLICATION"
        :onClick="showEnteredValue"
      />
    </div>
    <div class="number-pad__line">
      <number :title="0" :onClick="showEnteredValue" />
      <number :title="SERVISE_OPERATOR.SEPARATOR" :onClick="showEnteredValue"></number>
      <number :title="SERVISE_OPERATOR.ASSIGNMENT" :onClick="showResult"></number>
      <right-side-operator
        :title="MATH_OPERATOR.ADDITION"
        :onClick="showEnteredValue"
      ></right-side-operator>
    </div>
  </div>
</template>

<script>
import { TopOperator, Number, RightSideOperator } from './Button'
import { MATH_OPERATOR, SERVISE_OPERATOR } from './../constants'

export default {
  name: 'Screen',
  props: {
    showEnteredValue: Function,
    showResult: Function,
    deleteLastEnteredValue: Function,
    clearEnteredValues: Function,
  },
  components: {
    'top-operator': TopOperator,
    number: Number,
    'right-side-operator': RightSideOperator,
  },
  data() {
    return {
      MATH_OPERATOR: MATH_OPERATOR,
      SERVISE_OPERATOR: SERVISE_OPERATOR,
    }
  },
}
</script>

<style>
@media screen and (max-width: 720px) {
  .number-pad {
    width: 400px;
  }
}

@media screen and (max-width: 576px) {
  .number-pad {
    width: 300px;
  }
}

@media screen and (max-width: 300px) {
  .number-pad {
    width: 250px;
  }
}
</style>
