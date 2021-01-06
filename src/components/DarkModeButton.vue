<template>
  <button class="dark-mode-button" @click="toggleTheme">
    <span v-if="isLightTheme">🌙</span>
    <span v-else>☀️</span>
  </button>
</template>

<script>
const THEME_NAME = {
  LIGHT: 'light',
  DARK: 'dark',
}

export default {
  name: 'DarkModeButton',
  data() {
    return {
      themeName: THEME_NAME.LIGHT,
    }
  },
  computed: {
    isLightTheme() {
      return this.themeName === THEME_NAME.LIGHT
    },
  },
  methods: {
    toggleTheme: function () {
      this.themeName =
        this.themeName === THEME_NAME.LIGHT ? THEME_NAME.DARK : THEME_NAME.LIGHT

      this.setThemeNameInHtmlDataset()
      this.setThemeNameInLocalStorage()
    },
    setThemeNameInHtmlDataset: function () {
      document.querySelector('html').dataset['theme'] = this.themeName
    },
    setThemeNameInLocalStorage: function () {
      localStorage.setItem('themeName', this.themeName)
    },
    getThemeNameFromLocalStorage: function () {
      return localStorage.getItem('themeName')
    },
  },
  mounted() {
    this.themeName = this.getThemeNameFromLocalStorage() || THEME_NAME.LIGHT
    this.setThemeNameInHtmlDataset()
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

html[data-theme='light'] {
  --bg-color: #f4f4f4;
  --calc-bg-color: #000;
  --calc-screen-bg-color: #fff;
  --top-operator-button-bg-color: #f8f8f8;
  --num-button-bg-color: #fff;
  --right-side-operator-button-bg-color: #f27200;
  --font-color: #000;
}

html[data-theme='dark'] {
  --bg-color: #1f2022;
  --calc-bg-color: #fff;
  --calc-screen-bg-color: #262626;
  --top-operator-button-bg-color: #424242;
  --num-button-bg-color: #262626;
  --font-color: #fff;
}
</style>
