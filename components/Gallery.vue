<template>
  <div class='art'>
    <div class="gallery">
      <div class="photo" v-for="item of value" :key="item.slug">
        <NuxtLink :to="{ name: 'art-slug', params: { slug: item.slug } }">
          <img :src="require(`~/assets/images/${item.img}`)" :alt="item.alt" />
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
  max-width: 800px;
}
.art div.photo {
  margin: 5px;
  border: 1px solid #ccc;
  float: left;
  width: 250px;
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
  height: 80px;
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
