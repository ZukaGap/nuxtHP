<template>
  <div>
    <table class="rwd-table">
      <tr>
        <th>spell</th>
        <th>type</th>
        <th>effect</th>
      </tr>
      <Spell
        v-for="spell in spells"
        :key="spell._id"
        :spell="spell.spell"
        :type="spell.type"
        :effect="spell.effect"
      />
    </table>
  </div>
</template>

<script>
import axios from "axios";
import Spell from "../../components/Spell";
export default {
  components: {
    Spell,
  },
  data() {
    return {
      spells: [],
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
        `https://www.potterapi.com/v1/spells?key=${key}`,
        config
      );
      return { spells: res.data };
      //   console.log(res.data);
    } catch (error) {
      console.error(error);
    }
  },
  head() {
    return {
      title: "Spells",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Harry Potter All Spells",
        },
      ],
    };
  },
};
</script>

<style scoped>
.rwd-table {
  margin: 1em auto;
  min-width: 300px;
}
.rwd-table tr {
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
}
.rwd-table th {
  display: none;
}
.rwd-table td {
  display: block;
}
.rwd-table td:first-child {
  padding-top: 0.5em;
}
.rwd-table td:last-child {
  padding-bottom: 0.5em;
}
.rwd-table td:before {
  content: attr(data-th) ": ";
  font-weight: bold;
  width: 6.5em;
  display: inline-block;
}
@media (min-width: 480px) {
  .rwd-table td:before {
    display: none;
  }
}
.rwd-table th,
.rwd-table td {
  text-align: left;
}
@media (min-width: 480px) {
  .rwd-table th,
  .rwd-table td {
    display: table-cell;
    padding: 0.25em 0.5em;
  }
  .rwd-table th:first-child,
  .rwd-table td:first-child {
    padding-left: 0;
  }
  .rwd-table th:last-child,
  .rwd-table td:last-child {
    padding-right: 0;
  }
}
.rwd-table {
  background: #34495e;
  color: #fff;
  border-radius: 0.4em;
  overflow: hidden;
}
.rwd-table tr {
  border-color: #46637f;
}
.rwd-table th,
.rwd-table td {
  margin: 0.5em 1em;
}
@media (min-width: 480px) {
  .rwd-table th,
  .rwd-table td {
    padding: 1em !important;
  }
}
.rwd-table th,
.rwd-table td:before {
  color: #dd5;
}
</style>