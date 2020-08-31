<template>
  <nuxt-link :to="'characters/' + id">
    <p>{{ name }}</p>
  </nuxt-link>
</template>

<script>
export default {
  name: "Character",
  props: ["id", "name"],
};
</script>

<style scoped>
p {
  margin: 10px 0;
}

a {
  color: #fff;
  font-family: WizardWorldSimplified;
  font-size: 20px;
  padding: 10px 0;
  text-align: center;
}

a:hover {
  color: var(--orange);
}
</style>