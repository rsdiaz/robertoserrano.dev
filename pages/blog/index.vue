<template>
  <div>
    <Header :title="title" :subtitle="subtitle" />
    <section class="container pb-6">
      <p>
        En mi blog escribo artículos sobre desarrollo web y mi día a día
        tecnológico. Puedes encontrar artículos sobre tecnologías web como HTML,
        CSS, JavaScript, Node.js, herramientas de desarrollo, etc.
      </p>
      <p>
        Pero también escribo sobre otros temas como servidores NAS, Docker,
        GNU/Linux o simplemente artículos que quiero guardar para una futura
        referencia.
      </p>
    </section>
    <section class="container">
      <h2 class="title mb-5">
        📝 Últimos
        <span class="subtitle is-3">artículos</span>
      </h2>

      <div class="columns">
        <div class="column">
          <article
            v-for="(article, index) in articles"
            :key="index"
            class="post-list"
          >
            <p class="date is-size-7">{{ formatDate(article.createdAt) }}</p>
            <h2 class="title is-4">
              <NuxtLink :to="`/blog/${article.slug}`">
                {{ article.title }}
              </NuxtLink>
            </h2>
            <p>{{ article.description }}</p>
            <strong>
              <NuxtLink :to="`/blog/${article.slug}`"> Leer más</NuxtLink>
            </strong>
          </article>
        </div>
        <aside class="column is-3">
          <h3 class="title is-4">🔍 Buscar artículos</h3>
          <Search />
        </aside>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content('/blog').sortBy('createdAt', 'desc').fetch()
    return { articles }
  },
  data() {
    return {
      title: 'Blog',
      subtitle: 'Aquí encontrarás artículos sobre desarrollo web',
    }
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
  head() {
    return {
      title: `Roberto Serrano Diaz-Grande | ${this.title}`,
    }
  },
}
</script>
<style lang="scss">
@import '~/assets/scss/pages/blog-index.scss';
</style>
