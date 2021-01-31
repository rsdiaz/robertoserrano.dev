<template>
  <div>
    <Animation />
    <TopAngle />
    <ResponsiveNav />
    <section class="container">
      <Nav />
    </section>
    <section class="container">
      <header class="page-header">
        <p class="date is-size-7">{{ formatDate(article.createdAt) }}</p>
        <h1 class="title">
          {{ article.title }}
        </h1>
        <cite>{{ article.description }}</cite>
        <img class="image" :src="article.picture" :alt="article.alt" />
      </header>
    </section>
    <section class="container">
      <nuxt-content :document="article" />
      <!-- <TwitterShare :article="article" /> -->
    </section>
    <SocialList />
    <Footer />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('blog', params.slug).fetch()
    return { article }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
  },
  head() {
    return {
      title: `${this.article.title} | robertoserrano.dev`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.article.description,
        },
        // Open Graph
        {
          hid: 'og:title',
          property: 'og:title',
          content: this.article.title,
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.article.description,
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.article.title,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.article.description,
        },
      ],
    }
  },
}
</script>
<style lang="scss" scoped>
.section.blog-page {
  max-width: 960px;
  margin: 0 auto;
  padding: 1.5rem 1.5rem;
}

.card.author-card {
  margin: 0;
}

.nuxt-content {
  h2,
  h3,
  h4 {
    font-weight: bold;
    margin-top: 0.5rem;
    margin-bottom: 1.25rem;
    line-height: 1.25;
  }
  p {
    margin-bottom: 1.563rem;
    font-size: 1.125rem;
    line-height: 1.833em;
  }
}
.nuxt-content h2 {
  font-size: 1.875rem;
}
.nuxt-content h3 {
  font-size: 1.5rem;
}

.nuxt-content-highlight {
  margin: 1.2rem 0;
}

cite {
  display: block;
  margin-bottom: 1.5rem;
}
</style>
