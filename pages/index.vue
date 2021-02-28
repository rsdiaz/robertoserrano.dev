<template>
  <div>
    <Animation />
    <TopAngle />
    <ResponsiveNav />
    <Header :title="title" :subtitle="subtitle" />
    <section class="container pb-6">
      <p>
        Desde 2012, llevo desarrollando aplicaciones web y he ayudado a muchas
        personas a lograr cosas innovadoras en la Web. Principalmente trabajo
        con herramientas y frameworks modernos como Wordpress, VueJs, Angular...
      </p>
      <p>
        Comparto mi aprendizaje y conocimiento a traves de mi
        <nuxt-link to="/blog">blog</nuxt-link>, en el cual publico artículos
        sobre desarrollo web y mi día a día tecnológico.
      </p>
      <p>
        Cuando no estoy codificando o presionando botones, me encontrarás
        pescando, destripando dispositivos o disfrutando de la naturaleza.
      </p>
    </section>
    <section class="container">
      <h2 class="title">
        📝 Últimos
        <span class="subtitle is-3">artículos en el blog</span>
      </h2>
      <PostList :articles="articles" />
      <!-- <div
        v-for="(article, index) in articles"
        :key="index"
        class="container article post-list"
      >
        <div :style="[!index ? { display: 'flex' } : {}]">
          <a :href="`/blog/${article.slug}`">
            {{ article.title }}
          </a>
          <span v-if="!index" class="tag">NUEVO</span>
        </div>
        <div class="date is-size-7">{{ formatDate(article.createdAt) }}</div>
      </div> -->
    </section>
    <SocialList />
    <Footer />
  </div>
</template>
<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content('/blog')
      .without(['body', 'toc'])
      .sortBy('createdAt', 'desc')
      .fetch()
    return { articles }
  },
  data() {
    return {
      title: 'Roberto Serrano Diaz-Grande',
      subtitle: 'Desarrollador Web | Tarragona',
    }
  },
  methods: {
    head() {
      return {
        title:
          '🙋‍♂️ Roberto Serrano Diaz-Grande | 💻 Desarrollador Web en Tarragona',
      }
    },
  },
}
</script>
