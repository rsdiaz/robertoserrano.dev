<template>
  <div id="search">
    <input v-model="query" type="search" autocomplete="off" />
    <ul v-if="articles.length">
      <li
        v-for="article of articles"
        :key="article.slug"
        @click.prevent="cleanInput"
      >
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          {{ article.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      query: '',
      articles: [],
    }
  },
  watch: {
    async query(query) {
      if (!query) {
        this.articles = []
        return
      }

      this.articles = await this.$content('/blog')
        .only(['title', 'slug'])
        .sortBy('createdAt', 'asc')
        .limit(12)
        .search(query)
        .fetch()
    },
  },
  methods: {
    cleanInput() {
      this.query = null
    },
  },
}
</script>
<style lang="scss">
@import '~/assets/scss/components/search.scss';
</style>
