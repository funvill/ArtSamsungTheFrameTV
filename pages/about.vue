<template>
  <article class="about-page">
    <nuxt-content :document="about" />
  </article>
</template>

<style scoped>
</style>

<script>
export default {
  async asyncData({ $content, params }) {
    const about = await $content("about").fetch();

    return {
      about
    };
  },
};
</script>
