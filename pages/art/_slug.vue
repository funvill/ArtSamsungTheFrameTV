<template>
  <article class="art">
    <h1>{{ art.title }}</h1>
    <tags :tags="art.tags" />
    <div class="actions">
      <a :href="require(`~/assets/images/${art.img}`)" download
        ><div class="btn btn-primary">Download 💾</div></a
      >
    </div>
    <a :href="require(`~/assets/images/${art.img}`)" download
      ><img :src="require(`~/assets/images/${art.img}`)" :alt="art.alt"
    /></a>

    <strong>Resolution:</strong>
    <NuxtLink
      to="/about#why-are-the-images-all-the-resolution-of-38402160-169-ish"
      >3840×2160</NuxtLink
    >, <strong>Mid Journey prompt:</strong> {{ art.prompt }} <br />
    <NuxtLink to="/about#how-to-load-artwork-onto-the-samsung-the-frame-tv"
      >How to load artwork onto the Samsung 'The Frame' TV</NuxtLink
    >
  </article>
</template>

<style scoped>
.actions {
  text-align: center;
}
.art img {
  max-width: 100%;
  margin: 10px;
  padding: 10px;
  border: 10px solid black;
  border-radius: 8px;
  background-color: gray;
  display: block;
}
</style>

<script>
export default {
  async asyncData({ params }) {
    return {
      art: require("../../assets/data.json").filter(function (row) {
        return row.slug == params.slug;
      })[0],
    };
  },
};
</script>
