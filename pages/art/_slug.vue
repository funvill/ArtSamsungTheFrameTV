<template>
  <article class="art">
    <h1>{{ art.title }}</h1>
    <tags :tags="art.tags" />
    <div class="actions">
      <a :href="art.img" download>
        <div class="btn btn-primary">Download 💾</div>
      </a>
    </div>
    <a :href="art.img" download>
      <nuxt-img :src="art.img" :alt="art.title" preset="slug" />
    </a>

    <strong>📺 Resolution:</strong>
    <NuxtLink
      to="/about#why-are-the-images-all-the-resolution-of-38402160-169-ish"
      >3840x2160</NuxtLink
    >, <strong>📃 Mid Journey prompt :</strong> {{ art.prompt }} <br />
    <NuxtLink to="/about#how-to-load-artwork-onto-the-samsung-the-frame-tv"
      >❓ How to load artwork onto the Samsung 'The Frame' TV</NuxtLink
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
    let art = require("../../assets/data.json").filter(function (row) {
      return row.slug == params.slug;
    });

    if (art == undefined || art.lenght == 0) {
      art = [
        {
          title: "Error can not find",
          tags: "Error can not find",
          img: "Error can not find",
          prompt: "Error can not find",
        },
      ];
      // middleware({ redirect }) {
      //   return redirect('/art');
      // }
    }

    // Get the first and probably only result
    return {
      art: art[0],
    };
  },
};
</script>
