<template>
  <button class="button" @click="(e) => onClick(e.target.innerText)">
    {{ title }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    title: String,
    onClick: Function,
  },
}
</script>

<style>
.button {
  width: 90px;
  height: 75px;
  border: 0;
  color: var(--font-color);
  font-size: 1rem;
  outline: none;
}

.button:hover {
  opacity: 0.95;
}

@media screen and (max-width: 720px) {
  .button {
    width: 25%;
    font-size: 0.9rem;
  }
}
</style>
