<template>
  <nuxt-link :to="'characters/' + id">
    <div class="joke">
      <p>{{ name }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Character",
  props: ["id", "name"],
};
</script>

<style scoped></style>