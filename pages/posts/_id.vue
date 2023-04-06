<template>
  <div class="mt-4">
    <b-container>
      <b-row>
        <b-col>
          <div>
            <b-card :title="article.title">
              <b-card-text>
                {{ article.content }}
              </b-card-text>
            </b-card>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const article = await $axios.$get('http://localhost:8081/api/articles/'+ params.id)
    return { article }
  },
}
</script>
