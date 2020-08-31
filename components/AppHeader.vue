<template>
  <header class="header">
    <nuxt-link to="/">
      <h1>J. K. Rowling World</h1>
    </nuxt-link>
    <ul>
      <li>
        <nuxt-link to="/">Home</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/characters">Characters</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/houses">Houses</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/spells">Spells</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
};
</script>

<style scoped>
@font-face {
  font-family: WizardWorldSimplified;
  src: url("~static/WizardWorldSimplified-Kxr7.ttf");
}

.header {
  width: 100%;
  height: 70px;
  background-color: #18171a;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

h1 {
  color: var(--light);
  padding: 0 20px;
  font-size: 26px;
  font-weight: 900;
  font-family: WizardWorldSimplified;
}

h1:hover {
  color: var(--orange);
  transition: ease-in-out 450ms;
}

h1::selection {
  color: var(--light);
}

ul {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

ul li {
  list-style-type: none;
}

ul li a {
  margin: 0 20px;
  font-size: 26px;
  color: var(--light);
  font-family: WizardWorldSimplified;
}

ul li a:hover {
  color: var(--orange);
  border-bottom: 5px solid var(--orange);
  transition: all ease-in-out 450ms;
}

ul li:last-child {
  margin-right: 50px;
}
</style>
