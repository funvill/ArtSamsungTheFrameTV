<template>
  <article>
    <h1>Search Tag: {{ slug }}</h1>
    <gallery :value="results" />
  </article>
</template>

<style scoped></style>

<script>
import Gallery from "../../components/Gallery.vue";
export default {
  components: { Gallery },

  async asyncData({ params }) {
    return {
      results: require("../../assets/data.json").filter(function (row) {
        return row.tags.includes(params.slug);
      }),
      slug: params.slug,
    };
  },
};
</script>
