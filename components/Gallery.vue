<template>
  <div class="art">
    <div class="gallery">
      <div class="photo" v-for="item of value" :key="item.slug">
        <NuxtLink :to="{ name: 'art-slug', params: { slug: item.slug } }">
          <nuxt-img :src="item.img" :alt="item.title" preset="thumbnail"/>
        </NuxtLink>
        <div class="desc">
          <strong>{{ item.title }}</strong>
          <tags :tags="item.tags"></tags>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.gallery {
  margin: 0 auto;
  max-width: 960px;
}
.art div.photo {
  margin: 5px;
  border: 1px solid #ccc;
  float: left;
  width: 310px;
  height: 250px;
  border-radius: 8px;
}

.art div.photo:hover {
  border: 1px solid #777;
}

.art div.photo img {
  border-radius: 8px;
  width: 100%;
  height: auto;
}

.art div.desc {
  padding: 5px;
  text-align: center;
  overflow: hidden;
  text-overflow: ellipsis " [..]";
}
</style>
<script>
export default {
  props: {
    value: Array,
  },
};
</script>
