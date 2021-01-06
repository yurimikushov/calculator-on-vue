<template>
  <button
    class="dark-mode-button"
    @click="toggle"
  >
    {{ theme.name === THEME_NAME.DARK ? '☀️' : '🌙' }}
  </button>
</template>

<script>
export default {
  name: 'DarkModeButton',
  data() {
    return {
      theme: {
        name: 'light',
      },
      THEME_NAME: {
        LIGHT: 'light',
        DARK: 'dark',
      },
    }
  },
  methods: {
    toggle: () => console.log('toggle theme'),
  },
}
</script>

<style>
.dark-mode-button {
  border: none;
  background-color: transparent;
  font-size: 0.75rem;
  outline: 0;
}
</style>
