<template>
  <calc-button class="button_top-operator" :title="title" :onClick="onClick">
  </calc-button>
</template>

<script>
import Button from './Button.vue'

export default {
  name: 'TopOperator',
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
.button_top-operator {
  background-color: var(--top-operator-button-bg-color);
}
</style>
