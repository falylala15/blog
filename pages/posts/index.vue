<template>
  <div class="mt-4">
    <b-container>
      <b-row>
        <b-col>
          <h2>Liste des articles</h2>
          <div v-for="article in articles" :key="article.id" class="mb-2" >
            <b-card :title="article.title">
              <b-card-text>
                {{ article.content }}
              </b-card-text>
              <b-link :href="`/posts/${article.id}`" class="card-link">Voir l'article</b-link>
            </b-card>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      articles: []
    };
  },
  mounted() {
    this.fetchArticles();
  },
  methods: {
    async fetchArticles() {
      try {
        const response = await axios.get("http://localhost:8081/api/articles");
        this.articles = response.data;
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>
