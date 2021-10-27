<template>
  <div class="home">
    <h1 class="mt-3 text-h1 text-center">Blog</h1>
    <v-container style="width: 30vw">
      <v-divider></v-divider>
    </v-container>
    <v-container>
      <v-row no-gutters>
        <v-col
          v-for="(article, index) in articles"
          :key="article.id"
          cols="12"
          sm="4"
          class="d-flex"
          style="justify-content: space-evenly"
        >
          <Card
            :API="API_URL"
            :title="article.titre"
            :image="article.image.formats.thumbnail.url"
            :description="article.description"
            :class="{ 'mt-5': index % 3 == 1 }"
          />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import Card from "@/components/Card.vue";

export default {
  name: "Home",
  components: {
    Card,
  },
  methods: {
    async call(endpoint) {
      const request = await fetch(this.API_URL + endpoint);
      const data = await request.json();

      return data;
    },

    async fetchArticles() {
      this.API_URL = "http://localhost:1337";
      this.articles = await this.call("/articles");
    },
  },
  mounted() {
    this.fetchArticles();
  },
  data() {
    return {
      API_URL: "http://localhost:1337",
      articles: [],
    };
  },
};
</script>
