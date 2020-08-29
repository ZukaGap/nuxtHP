<template>
  <div class="home">
    <h2>Discover your Hogwarts house</h2>
    <input
      v-on:click="dicoverHouse"
      type="button"
      value="Discover Your House"
    />
    <p>{{ house }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      house: ""
    };
  },
  methods: {
    async dicoverHouse() {
      const config = {
        headers: {
          Accept: "application/json"
        }
      };

      try {
        const res = await axios.get(
          "https://www.potterapi.com/v1/sortingHat",
          config
        );
        this.house = res.data;
        console.log("res.data");
      } catch (error) {
        console.error(error);
      }
    }
  },
  head() {
    return {
      title: "Harry Potter",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "J. K. Rowling World"
        }
      ]
    };
  }
};
</script>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  height: 500px;
}

h2 {
  text-align: center;
}
</style>
