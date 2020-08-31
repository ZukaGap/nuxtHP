<template>
  <div class="character">
    <nuxt-link to="/characters" class="back">Back To Characters</nuxt-link>
    <table>
      <tr v-for="key in Object.keys(strippedCharacter)" :key="key">
        <th>{{ beautifyObjectKey(key) }}:</th>
        <td>{{ character[key] }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";

const exclude = ["_id", "__v"];

export default {
  data() {
    return {
      character: {},
    };
  },
  computed: {
    strippedCharacter() {
      const stripped = { ...this.character };
      for (let ex of exclude) {
        delete stripped[ex];
      }
      return stripped;
    },
  },
  methods: {
    beautifyObjectKey(key) {
      const words = key.split(/(?=[A-Z])/);
      words[0] = words[0].charAt(0).toUpperCase() + words[0].slice(1);
      return words.join(" ");
    },
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
.character {
  width: 100%;
  height: 100%;
  margin: 2rem 0;
}

.back {
  color: var(--light);
  font-family: WizardWorldSimplified;
  font-size: 20px;
  margin-left: 20px;
  margin-top: 20px;
}

.back:hover {
  color: var(--blue);
}

table {
  font-family: WizardWorldSimplified;
  font-size: 20px;
  color: var(--light);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

th {
  font-size: 24px;
}

td:hover,
th:hover {
  color: var(--orange);
}
</style>