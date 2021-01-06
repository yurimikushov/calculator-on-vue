<template>
  <div class="screen">
    <dark-mode-button class="position_top-left pt-10 pl-10"></dark-mode-button>
    <span class="screen__preview-result position_top-right pt-10 pr-10 pl-50">
      {{ previewResult }}
    </span>
    <input
      class="screen__result position_bottom"
      type="text"
      :value="result"
      placeholder="0"
      readonly
    />
  </div>
</template>

<script>
import DarkModeButton from './DarkModeButton.vue'

export default {
  name: 'Screen',
  props: {
    previewResult: String,
    result: String,
  },
  components: {
    'dark-mode-button': DarkModeButton,
  },
}
</script>

<style>
.screen {
  position: relative;
  width: 100%;
  height: 125px;
  background-color: var(--calc-screen-bg-color);
  font-family: Arial, Helvetica, sans-serif;
}

.screen__preview-result {
  width: calc(100% - 60px);
  border: 0;
  color: var(--font-color);
  font-size: 1rem;
  opacity: 0.6;
  outline: none;
  text-align: right;
}

.screen__result {
  width: calc(100% - 20px);
  padding: 0 10px;
  border: 0;
  background-color: inherit;
  color: var(--font-color);
  font-size: 1.4rem;
  outline: none;
  text-align: right;
}
</style>
