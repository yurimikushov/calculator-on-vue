<template>
  <calc-button
    class="button_right-side-operator" 
    :title="title" 
    :onClick="onClick" >
  </calc-button>
</template>

<script>
import Button from './Button.vue'

export default {
  name: 'RightSideOperator',
  props: {
    title: String,
    onClick: Function,
  },
  components: {
    'calc-button': Button,
  },
}
</script>

<style>
.button_right-side-operator {
  background-color: var(--right-side-operator-button-bg-color);
  color: #fff;
}
</style>
