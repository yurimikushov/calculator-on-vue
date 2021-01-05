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
import Screen from './Screen.vue'
import NumPad from './NumPad.vue'

export default {
  name: 'Calculator',
  components: {
    'screen': Screen,
    'num-pad': NumPad,
  },
  data() {
    return {
      previewResult: '',
      enteredValues: '',
    }
  },
  methods: {
    showEnteredValue: function (value) {
      console.log('showEnteredValue', value)
    },
    showResult: function (value) {
      console.log('showResult', value)
    },
    deleteLastEnteredValue: function (value) {
      console.log('deleteLastEnteredValue', value)
    },
    clearEnteredValues: function (value) {
      console.log('clearEnteredValues', value)
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
