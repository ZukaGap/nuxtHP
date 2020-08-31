<template>
  <div>
    <Character
      v-for="character in characters"
      :key="character._id"
      :id="character._id"
      :name="character.name"
    />
  </div>
</template>

<script>
import axios from "axios";
import Character from "../../components/Character";

export default {
  components: {
    Character,
  },
  data() {
    return {
      characters: [],
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start();
      setTimeout(() => this.$nuxt.$loading.finish(), 400);
    });
  },
  async asyncData({ params }) {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };

    try {
      var key = "$2a$10$2LsY3uD/ErHbexqAmZB6cu.yzSQ52xet/b18Imkv4nSocwHlhmzw2";
      const res = await axios.get(
        `https://www.potterapi.com/v1/characters?key=${key}`,
        config
      );
      return { characters: res.data };
      //   console.log(res.data);
    } catch (error) {
      console.error(error);
    }
  },
  head() {
    return {
      title: "Characters",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Harry Potter All Charachters",
        },
      ],
    };
  },
};
</script>

<style scoped>
</style>