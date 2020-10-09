<template>
  <div>
    <TopAngle />
    <div class="container">
      <div class="columns is-variable pb-3 pt-5">
        <div class="column is-2">
          <nuxt-link to="/" class="button">Home</nuxt-link>
        </div>
        <div class="column is-2">
          <nuxt-link to="/sobre-mi" class="button">Sobre mí</nuxt-link>
        </div>
        <div class="column is-2">
          <nuxt-link to="/contacto" class="button">Contacto</nuxt-link>
        </div>
      </div>
      <div class="columns">
        <section class="column">
          <header class="page-header">
            <h1 class="title">Blog</h1>
            <h2 class="subtitle is-3">
              Aquí encontrarás mis artículos publicados
            </h2>
            <p>
              En mi blog escribo artículos sobre desarrollo web y mi día a día
              tecnológico. Puedes encontrar artículos sobre tecnologías web como
              HTML, CSS, JavaScript, Node.js, herramientas de desarrollo, etc.
            </p>
            <p>
              Pero también escribo sobre otros temas como servidores NAS,
              Docker, GNU/Linux o simplemente artículos que quiero guardar para
              una futura referencia.
            </p>
          </header>
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
        </section>
        <aside class="column is-3">
          <h3 class="title is-4">Buscar artículos</h3>
          <Search />
        </aside>
      </div>
      <SocialList />
      <ColorMode />
      <Footer />
    </div>
  </div>
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
  head: {
    title: 'Roberto Serrano | Blog | robertoserrano.dev',
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
