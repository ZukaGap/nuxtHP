<template>
  <div>
    <AppHeader />
    <Nuxt />
  </div>
</template>

<script>
import AppHeader from "../components/AppHeader";

export default {
  components: {
    AppHeader,
  },
};
</script>

<style>
html {
  font-family: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono",
    "Courier New", monospace;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background-color: #f7f6f5;
}

a {
  text-decoration: none;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
</style>
