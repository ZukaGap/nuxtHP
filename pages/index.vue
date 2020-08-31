<template>
  <div class="home">
    <h2>Discover your Hogwarts house</h2>
    <img src="~static/snitch.png" />
    <div class="house">
      <input class="spinbtn" v-on:click="dicoverHouse" type="button" value="Discover Your House" />
      <p>{{house}}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      house: "Misterry",
    };
  },
  methods: {
    async dicoverHouse() {
      const config = {
        headers: {
          Accept: "application/json",
        },
      };

      try {
        const res = await axios.get(
          "https://www.potterapi.com/v1/sortingHat",
          config
        );
        this.house = res.data;
      } catch (error) {
        console.error(error);
      }
    },
  },
  head() {
    return {
      title: "Harry Potter",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "J. K. Rowling World",
        },
      ],
    };
  },
};
</script>

<style scoped>
@font-face {
  font-family: WolfpackHalloweed;
  src: url("~static/WolfpackHalloweed-EaGOl.otf");
}

.home {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  position: relative;
  height: 500px;
  margin: 2rem 0;
}

h2 {
  text-align: center;
  color: #f8f9fa;
  font-size: 5rem;
  letter-spacing: 5px;
  font-family: FontasticBeast;
}

h2::selection {
  color: #fd7e14;
}

.house {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  width: 100%;
}

.spinbtn {
  font-family: WolfpackHalloweed;
  letter-spacing: 3px;
  font-size: 20px;
  outline: none;
  color: #fd7e14;
  background-color: transparent;
  border: 2px solid #fd7e14;
  cursor: pointer;
}
.spinbtn:active {
  color: #f8f9fa;
  background: rgb(253, 164, 20);
  background: radial-gradient(
    circle,
    rgba(253, 164, 20, 1) 20%,
    rgba(253, 126, 20, 1) 80%
  );
}

p {
  font-family: WolfpackHalloweed;
  letter-spacing: 3px;
  font-size: 3rem;
  color: #f8f9fa;
}

p::selection {
  color: #fd7e14;
}
</style>
