<template>
  <section class="newsfeed">
    <NewsFeed />
  </section>
</template>

<script>
import NewsFeed from "./NewsFeed.vue";

export default {
  name: "HomePage",
  props: {
    news: Object
  },
  components: { NewsFeed },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  color: #42b983;
}

/* media queries */
@media screen and (min-width: 1000px) {
  .newsfeed {
    padding: 24px 20%;
    margin-top: 40px;
  }
}
</style>
