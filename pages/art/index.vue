<template>
  <div class="art">
    <h2>Art Index</h2>
    <gallery :value="results" />
  </div>
</template>

<script>
import Gallery from "../../components/Gallery.vue";
export default {
  components: { Gallery },  
  async asyncData({ $content, params }) {
    const results = await $content("arts")
      .sortBy("createdAt", "asc")
      .only(["title", "slug", "tags", "img"])
      .fetch();
    return {
      results,
      slug: params.slug,
    };
  },
};
</script>
