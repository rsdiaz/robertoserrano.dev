<template>
  <div>
    <div class="columns">
      <div class="hero is-fullheight column column-left is-hidden-touch">
        <div class="container">
          <LogoBig />
          <h1 class="site-title">robertoserrano.dev</h1>
          <h2><nuxt-link to="/">Home</nuxt-link></h2>
          <h2><nuxt-link to="/blog">Blog</nuxt-link></h2>
          <h2><nuxt-link to="/sobre-mi">Sobre mí</nuxt-link></h2>
          <h2><nuxt-link to="/contacto">Contacto</nuxt-link></h2>
        </div>
      </div>
      <div class="hero is-fullheight column column-right">
        <div class="container hero is-fullheight-with-navbar">
          <h1 id="home-title" class="title is-1 is-spaced has-text-centered">
            Hola!
          </h1>
          <figure class="image">
            <img
              class="profile-pic is-rounded has-shadow"
              src="https://res.cloudinary.com/rserrano/image/upload/v1598652059/roberto-serrano-desarrolloweb-tarragona.jpg"
              alt="Roberto Serrano desarrollo web Tarragona"
            />
          </figure>
          <h2 class="subtitle">
            <p>Mi nombre es Roberto Serrano.</p>
            <p>Soy un desarrollador web viviendo en Tarragona, España.</p>
            <p>
              Desde 2012, llevo desarrollando aplicaciones web y he ayudado a
              muchas personas a lograr cosas innovadoras en la Web.
            </p>
            <p>
              Principalmente trabajo con herramientas y frameworks modernos como
              Wordpress, VueJs, Angular...
            </p>
            <p>
              Puedes leer más
              <a href="/sobre-mi">sobre mi</a> o consultar algunos de mis
              <a href="/sobre-mi">proyectos.</a>
            </p>
          </h2>
          <Social />
          <ColorMode />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content }) {
    const docs = await $content('/blog').without(['body', 'toc']).fetch()
    return { docs }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
  },
  head: {
    title:
      '🙋‍♂️ Roberto Serrano | 💻 Desarrollador Web en Tarragona | 🌍 robertoserrano.dev',
  },
}
</script>
