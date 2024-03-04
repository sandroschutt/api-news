<template>
  <article v-if="newsData">
    <div class="news-header">
      <h2 class="title">
        <a :href="`${newsData.url}`">
          {{ newsData.title }}
        </a>
      </h2>
      <img
        v-if="newsData.urlToImage !== null"
        class="featured-image"
        :src="`${newsData.urlToImage}`"
      />
      <div class="news-meta">
        <h3 class="author">{{ newsData.author }}</h3>
        <h3 class="vehicle-name">{{ newsData.source.name }}</h3>
        <h5 class="published-date">{{ newsData.publishedAt }}</h5>
      </div>
    </div>
    <div class="news-excerpt">
      <p>{{ newsData.description }}</p>
      <a :href="`${newsData.url}`">{{ "Leia mais >" }}</a>
    </div>
  </article>
</template>

<script>
import { onMounted, ref, watch } from "vue";

export default {
  name: "SinglePost",
  props: ["news"],
  async setup(props) {
    const newsData = ref(null);

    onMounted(() => {
      newsData.value = props.news;
    });

    watch(
      () => props.news,
      (newValue) => {
        if (newValue) {
          newsData.value = newValue;
        }
      }
    );

    return { newsData };
  },
};
</script>

<style scoped>
article {
  margin: 40px auto;
}

a {
  color: #2a6d4f;
}

/* custom classes */
.featured-image {
  width: 100%;
  margin: 24px auto 12px;
  background-color: #cccccc;
  border-radius: 8px;
}

.title {
  margin: 0 auto;
  font-size: 1.8em;
  font-weight: bold;
}

.title a {
  color: #000000 !important;
}

.news-meta {
  margin-bottom: 12px;
  display: flex;
  flex-wrap: wrap;
}

.author {
  padding-right: 8px;
}

.vehicle-name {
  padding-left: 8px;
  padding-right: 8px;
  border-left: 1px solid black;
  border-right: 1px solid black;
}

.published-date {
  padding-left: 8px;
  align-self: center;
}

.title,
.author,
.vehicle-name,
.published-date {
  text-align: left;
  font-weight: 500;
  color: #2a6d4f;
}

.news-excerpt {
  margin-bottom: 64px;
}

.news-excerpt p {
  text-align: left;
  margin-bottom: 12px;
}
 .news-excerpt a {
  font-weight: bold;
 }
</style>
