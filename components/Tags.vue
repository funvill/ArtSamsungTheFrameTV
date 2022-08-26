<template>
  <div><span v-html="MakeTagsIntoLinks(tags)"></span></div>
</template>

<script>
export default {
  methods: {
    MakeTagsIntoLinks(tags) {
      let output = "";
      if (typeof tags === "string") {
        let tagArray = tags.split(",");
        tagArray.forEach((tag) => {
          if (tag.length > 0) {
            output +=
              "<a href='/tag/" + tag.trim() + "'>#" + tag.trim() + "</a>, ";
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
