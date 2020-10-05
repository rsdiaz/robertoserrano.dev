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
            Pero también escribo sobre otros temas como servidores NAS, Docker,
            GNU/Linux o simplemente artículos que quiero guardar para una futura
            referencia.
          </p>
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
          <h3 class="title is-4">Categorias</h3>
          <p># HTML/CSS</p>
          <p># JavaScript</p>
          <p># NodeJs</p>
          <p># Vue</p>
          <p># Servidores NAS</p>
          <p># Docker</p>
        </aside>
      </div>
      <SocialList />
      <ColorMode />
      <Footer />
    </div>
  </div>
  <!-- <section class="section blog-page">
    <h1 class="page-title title is-1 has-text-centered">Blog</h1>
    <div class="columns content blog-list-wrapper">
      <div
        v-for="(article, index) in articles"
        :key="index"
        class="card column blog-list"
        :class="[isArticleFull(index) ? 'is-full' : 'is-half']"
      >
        <div class="card-image blog-list-image">
          <figure class="image is-4by3">
            <clazy-load :src="article.picture" margin="40px">
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
            <NuxtLink :to="`/blog/${article.slug}`">
              {{ article.title }}
            </NuxtLink>
          </h2>
          <p class="date">{{ formatDate(article.createdAt) }}</p>
          <p>{{ article.description }}</p>
          <div class="blog-excerpt-bottom">
            <strong>
              <NuxtLink :to="`/blog/${article.slug}`"> Leer más</NuxtLink>
            </strong>
          </div>
        </div>
      </div>
      <author :author="articles[0].author" />
    </div>
    <Footer />
    <ColorMode />
  </section> -->
</template>
<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content('/blog').sortBy('createdAt', 'desc').fetch()
    const categories = await $content('/blog').only(['category']).fetch()
    console.log(categories)
    return { articles, categories }
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
