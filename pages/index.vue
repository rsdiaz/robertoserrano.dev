<template>
  <div>
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
        <span class="subtitle is-3">artículos</span>
      </h2>
      <PostList :articles="articles" />
      <nuxt-link to="/blog" class="button">Leer todos los artículos</nuxt-link>
    </section>
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
  methods: {},
  head() {
    return {
      title: 'Roberto Serrano Diaz-Grande | 💻 Desarrollador Web en Tarragona',
    }
  },
}
</script>
