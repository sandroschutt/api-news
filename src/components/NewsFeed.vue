<template>
  <div class="searchbox">
    <input
      type="text"
      name="search"
      placeholder="Busque por notícias"
      v-model="searchText"
    />
    <button type="button" @click="fetchSearchResults()">Buscar</button>
  </div>

  <suspense>
    <ul id="feed">
      <li v-for="(post, index) in news" :key="index">
        <SinglePost :news="post" />
      </li>
    </ul>
  </suspense>

  <ul class="page-list">
    <li>
      <p
        @click="
          currentPage > 1
            ? handleNavigatePages('decrease')
            : (currentPage.value = 10)
        "
      >
        {{ "<" }}
      </p>
    </li>
    <li v-for="p in 10">
      <p
        :class="[currentPage === p ? 'current-page' : '']"
        @click="
          () => {
            currentPage = p;
            scrollToTop();
          }
        "
      >
        {{ p }}
      </p>
    </li>
    <li>
      <p
        @click="
          currentPage < 10
            ? handleNavigatePages('increase')
            : (currentPage.value = 1)
        "
      >
        {{ ">" }}
      </p>
    </li>
  </ul>
</template>

<script>
import { onMounted, watch, ref } from "vue";
import SinglePost from "@/components/SinglePost.vue";

const apiKey = import.meta.env.VITE_API_KEY;

export default {
  name: "NewsFeed",
  setup() {
    const news = ref([]);
    const currentPage = ref(1);
    const searchText = ref("");

    const reqOptions = ref({
      q: "programming",
      apiKey: apiKey,
      pageSize: 10,
      language: "pt"
    });

    async function fetchNewsPage() {
      try {
        const req = await fetch(
          `https://newsapi.org/v2/everything?q=${reqOptions.value.q}&apiKey=${reqOptions.value.apiKey}&pageSize=${reqOptions.value.pageSize}&page=${currentPage.value}&language=${reqOptions.value.language}`
        );

        const res = await req.json();

        if (res.status !== "error" && res.totalResults > 0) {
          news.value = res.articles;
          console.log(res);
        } else throw new Error(`Nenhum resultado encontrado para: ${searchText.value}`);
      } catch (error) {
        alert(error);
      }
    }

    async function fetchSearchResults() {
      reqOptions.value.q = searchText.value;
      currentPage.value = 1;
      fetchNewsPage();
    }

    function scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });
    }

    function handleNavigatePages(action = String) {
      if (action === "increase") {
        currentPage.value++;
        scrollToTop();
      } else if (action === "decrease") {
        currentPage.value--;
        scrollToTop();
      }
    }

    watch(currentPage, fetchNewsPage);
    onMounted(fetchNewsPage);

    return {
      news,
      currentPage,
      searchText,
      scrollToTop,
      handleNavigatePages,
      fetchSearchResults,
    };
  },
  components: {
    SinglePost,
  },
};
</script>

<style scoped>
.searchbox {
  justify-content: space-between;
  border: 1px solid #efefef;
}

.searchbox input {
  padding: 8px;
  width: 80%;
}

.searchbox input:focus,
.searchbox button:focus {
  outline: #efefef;
}

.searchbox button {
  width: 20%;
}

.searchbox button:hover {
  cursor: pointer;
  background-color: #b9b9b9;
  color: white;
}

.searchbox input,
.searchbox button {
  border: none;
}

ul {
  padding-left: 0 ;
}

ul li {
  list-style: none;
}

.page-list,
.searchbox {
  display: flex;
  flex-wrap: wrap;
}

.page-list {
  justify-content: center;
}

.page-list li {
  padding: 12px;
  color: #42b983;
  font-size: 20px;
  font-weight: 500;
}

.page-list li:hover {
  cursor: pointer;
  color: #52df9f;
}

.page-list p {
  padding: none;
}

.current-page {
  font-weight: bold;
  border-bottom: 2px solid #42b983;
}
</style>
