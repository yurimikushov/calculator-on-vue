<template>
  <calc-button class="button_number" :title="title" :onClick="onClick"> </calc-button>
</template>

<script>
import Button from './Button.vue'

export default {
  name: 'Number',
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
.button_number {
  background-color: var(--num-button-bg-color);
}
</style>
