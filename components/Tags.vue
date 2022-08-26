<template>
  <div>
    <span v-for="TagSlug in cleanTags(tags)" :key="TagSlug" >
      <NuxtLink :to="{ path: `/tag/${TagSlug}` }">#{{ TagSlug }}</NuxtLink>, 
    </span>
  </div>
</template>

<script>
export default {
  methods: {
    cleanTags(tags) {
      let output = [];
      if (typeof tags === "string") {
        let tagArray = tags.split(",");
        tagArray.forEach((tag) => {
          if (tag.length > 0) {
            output.push(tag.trim());
          }
        });
      }
      return output;
    },
  },
  props: {
    tags: String,
  },
};
</script>
