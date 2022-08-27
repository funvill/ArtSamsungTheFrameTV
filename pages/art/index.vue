<template>
  <div class="art">
    <h2>Art Index</h2>
    <gallery :value="results" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      results: require("../../assets/data.json"),
    };
  },
};
</script>
