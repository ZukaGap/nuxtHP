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
  name: "AppHeader"
};
</script>

<style scoped>
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
  color: #f8f9fa;
  padding: 0 20px;
  font-size: 26px;
  font-weight: 900;
}

h1::selection {
  color: #f8f9fa;
}

ul {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

ul li a {
  margin: 0 20px;
  font-size: 26px;
  color: #f8f9fa;
}

ul li a:hover {
  color: #fd7e14;
  border-bottom: 5px solid #fd7e14;
}

ul li:last-child {
  margin-right: 50px;
}
</style>
