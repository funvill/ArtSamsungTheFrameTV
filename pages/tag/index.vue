<template>
  <article class="tag">
    <h2>Tag Index</h2>
    <tags :tags="tags"></tags>
  </article>
</template>

<style scoped></style>

<script>
export default {
  async asyncData({ $content, params }) {
    const allTags = await $content("arts")
      .only(["tags"])
      .sortBy("createdAt", "asc")
      .fetch();

    let allTagsAsArray = [];
    allTags.forEach((artPage) => {
      let cleanedUpTags = artPage.tags.split(",").map((element) => {
        return element.trim();
      });

      // Add each cleaned up tag to the all tags
      // We only want the unique tags
      cleanedUpTags.forEach((tag) => {
        if (tag.length > 0) {
          if (allTagsAsArray.indexOf(tag) == -1) {
            allTagsAsArray.push(tag);
          }
        }
      });
    });

    return {
      tags: allTagsAsArray.join(","),
    };
  },
};
</script>
