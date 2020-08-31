<template>
  <tr>
    <td>{{spell}}</td>
    <td>{{type}}</td>
    <td>{{effect}}</td>
  </tr>
</template>
<script>
export default {
  props: ["spell", "type", "effect"],
};
</script>
<style scoped>
.rwd-table th,
.rwd-table td {
  padding: 1em !important;
}
</style>