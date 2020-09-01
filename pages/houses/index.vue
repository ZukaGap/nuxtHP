<template>
  <div class="houses">
    <img class="house" src="../../static/gryffindor.jpg" alt />
    <img class="house" src="../../static/slytherin.jpg" alt />
    <img class="house" src="../../static/hufflepuff.jpg" alt />
    <img class="house" src="../../static/ravenclaw.jpg" alt />
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "House",
    };
  },
};
</script>

<style scoped>
.houses {
  height: 350px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.house {
  height: 250px;
  width: 200px;
}

.house:hover {
  height: 300px;
  width: 200px;
}
</style>