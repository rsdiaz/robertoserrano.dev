<template>
  <section class="section blog-page has-background-white-ter">
    <h1 class="title is-1 has-text-centered">Blog</h1>
    <div class="columns content blog-list-wrapper">
      <div
        v-for="(article, index) in articles"
        :key="index"
        class="card column blog-list"
        :class="[isArticleFull(index) ? 'is-full' : 'is-half']"
      >
        <div class="card-image blog-list-image">
          <figure class="image is-4by3">
            <clazy-load :src="article.picture">
              <transition name="fade">
                <img :src="article.picture" />
              </transition>
              <transition slot="placeholder" name="fade">
                <div slot="placeholder">Loading....</div>
              </transition>
            </clazy-load>
          </figure>
        </div>
        <div class="blog-excerpt">
          <h2 class="title is-4 mt-4">
            <NuxtLink :to="`/blog/${article.slug}`" class="has-text-primary">
              {{ article.title }}
            </NuxtLink>
          </h2>
          <p class="date">{{ formatDate(article.createdAt) }}</p>
          <p>{{ article.description }}</p>
          <div class="blog-excerpt-bottom">
            <NuxtLink :to="`/blog/${article.slug}`" class="has-text-primary">
              Leer más
            </NuxtLink>
          </div>
        </div>
      </div>
      <!-- content author component -->
      <author :author="articles[0].author" />
    </div>
    <Footer />
  </section>
</template>
<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content('/blog').sortBy('createdAt', 'desc').fetch()
    return { articles }
  },
  methods: {
    goToArticle(slug) {
      return this.$router.push({ path: `/blog/${slug}` })
    },
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
    isArticleFull(index) {
      return Number.isInteger(Math.pow(index, 3) / 3)
    },
  },
}
</script>
<style lang="scss">
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
section.section {
  h1.title {
    margin-bottom: 3rem;
  }
  h2.title {
    margin-bottom: 0.5714em;
  }
}
.content {
  figure {
    margin-left: 0;
    margin-right: 0;
  }
}
.blog-list-wrapper {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.blog-list-image {
  img {
    border-radius: 2px;
  }
}
.blog-excerpt {
  .date {
    font-size: 0.85rem;
  }
}
</style>
