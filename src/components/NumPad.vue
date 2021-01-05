<template>
  <div class="calc-button-pad">
    <div class="calc-button-pad__line">
      <calc-button
        className="button_top-operators"
        :title="SERVISE_OPERATOR.CLEAR"
        :onClick="clearEnteredValues"
      ></calc-button>
      <calc-button
        className="button_top-operators"
        :title="MATH_OPERATOR.OPENING_PARENTHESIS"
        :onClick="showEnteredValue"
      ></calc-button>
      <calc-button
        className="button_top-operators"
        :title="MATH_OPERATOR.CLOSING_PARENTHESIS"
        :onClick="showEnteredValue"
      ></calc-button>
      <calc-button
        className="button_top-operators"
        :title="SERVISE_OPERATOR.DELETE"
        :onClick="deleteLastEnteredValue"
      ></calc-button>
    </div>
    <div class="calc-button-pad__line">
      <calc-button className="button_numbers" :title="7" :onClick="showEnteredValue"></calc-button>
      <calc-button className="button_numbers" :title="8" :onClick="showEnteredValue"></calc-button>
      <calc-button className="button_numbers" :title="9" :onClick="showEnteredValue"></calc-button>
      <calc-button
        className="button_right-side-operators"
        :title="MATH_OPERATOR.DIVISION"
        :onClick="showEnteredValue"
      ></calc-button>
    </div>
    <div class="calc-button-pad__line">
      <calc-button className="button_numbers" :title="4" :onClick="showEnteredValue"></calc-button>
      <calc-button className="button_numbers" :title="5" :onClick="showEnteredValue"></calc-button>
      <calc-button className="button_numbers" :title="6" :onClick="showEnteredValue"></calc-button>
      <calc-button
        className="button_right-side-operators"
        :title="MATH_OPERATOR.SUBSRTACTION"
        :onClick="showEnteredValue"
      ></calc-button>
    </div>
    <div class="calc-button-pad__line">
      <calc-button className="button_numbers" :title="1" :onClick="showEnteredValue"></calc-button>
      <calc-button className="button_numbers" :title="2" :onClick="showEnteredValue"></calc-button>
      <calc-button className="button_numbers" :title="3" :onClick="showEnteredValue"></calc-button>
      <calc-button className="button_right-side-operators" :title="MATH_OPERATOR.MULTIPLICATION" :onClick="showEnteredValue" />
    </div>
    <div class="calc-button-pad__line">
      <calc-button className="button_numbers" :title="0" :onClick="showEnteredValue" />
      <calc-button
        className="button_numbers" :title="SERVISE_OPERATOR.SEPARATOR"
        :onClick="showEnteredValue"
      ></calc-button>
      <calc-button
        className="button_numbers" :title="SERVISE_OPERATOR.ASSIGNMENT"
        :onClick="showResult"
      ></calc-button>
      <calc-button
        className="button_right-side-operators" 
        :title="MATH_OPERATOR.ADDITION"
        :onClick="showEnteredValue"
      ></calc-button>
    </div>
  </div>
</template>

<script>
import Button from './Button.vue'
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
    'calc-button': Button,
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
  .calc-button-pad {
    width: 400px;
  }
}

@media screen and (max-width: 576px) {
  .calc-button-pad {
    width: 300px;
  }
}

@media screen and (max-width: 300px) {
  .calc-button-pad {
    width: 250px;
  }
}
</style>
