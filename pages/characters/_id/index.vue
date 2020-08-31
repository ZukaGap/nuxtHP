<template>
  <div>
    <nuxt-link to="/characters" class="back">Back To Jokes</nuxt-link>
    <h2>{{ character }}</h2>
    <hr />
    <small>Joke ID: {{ $route.params.id }}</small>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      character: {},
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };

    try {
      var key = "$2a$10$2LsY3uD/ErHbexqAmZB6cu.yzSQ52xet/b18Imkv4nSocwHlhmzw2";
      const res = await axios.get(
        `https://www.potterapi.com/v1/characters/${this.$route.params.id}?key=${key}`,
        config
      );
      this.character = res.data;
    } catch (error) {
      console.error(error);
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start();
      setTimeout(() => this.$nuxt.$loading.finish(), 400);
    });
  },
  head() {
    return {
      title: this.joke,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for music play",
        },
      ],
    };
  },
};
</script>

<style scoped>
</style>