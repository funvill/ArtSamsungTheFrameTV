<template>
  <article>
    <h1>Search Tag: {{slug}}</h1>
    <gallery :value="results" />
    
  </article>
</template>

<style scoped></style>

<script>
import Gallery from '../../components/Gallery.vue';
export default {
  components: { Gallery },
  async asyncData({ $content, params }) {
    const results = await $content("arts")
      .where({ tags: { $contains: params.slug} })
      .only(["title", "slug", "tags", "img"])
      .fetch();
    return {
      results,
      slug: params.slug
    };
  },
};
</script>
