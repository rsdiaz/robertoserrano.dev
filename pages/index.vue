<template>
  <div>
    <div class="container">
      <div class="logo">
        <h1 class="title">Roberto Serrano Diaz-Grande</h1>
        <h2 class="subtitle is-3">Desarrollador Web | Tarragona</h2>
        <p>
          Desde 2012, llevo desarrollando aplicaciones web y he ayudado a muchas
          personas a lograr cosas innovadoras en la Web. Principalmente trabajo
          con herramientas y frameworks modernos como Wordpress, VueJs,
          Angular...
        </p>
        <p>
          Cuando no estoy codificando o presionando píxeles, me encontrarás en
          el gimnasio, jugando al fútbol o anotando más de par en el campo de
          golf.
        </p>
        <div class="columns">
          <div class="column is-2">
            <a href="/sobre-mi" class="button">Contacto</a>
          </div>
          <div class="column is-2">
            <a href="/sobre-mi" class="button">Sobre mí</a>
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="columns is-variable is-8">
        <div class="column frontend">
          <h2 class="is-size-3 has-text-weight-bold mb-4">Frontend</h2>
          <ul>
            <li>
              <a href="">
                CSS Grid Template
                <span>Ejemplo de pagina web usando CSS Grid</span>
              </a>
            </li>
            <li>
              <a href="">
                Login page example
                <span>Pagina de inicio de sesión con CSS Grid y Flexbox</span>
              </a>
            </li>
          </ul>
        </div>
        <div class="column backend">
          <h2 class="is-size-3 has-text-weight-bold mb-4">Backend</h2>
          <ul>
            <li>
              <a href="">node-clima</a>
              <span>Modulo NodeJs escrito en TypeScript</span>
            </li>
          </ul>
        </div>
        <div class="column">
          <h2 class="is-size-3 has-text-weight-bold mb-4">Artículos</h2>
        </div>
      </div>
    </div>
    <!-- <div class="columns">
      <div class="hero is-fullheight column column-left is-hidden-touch">
        <div class="container">
          <LogoBig />
          <h1 class="site-title">robertoserrano.dev</h1>
          <h2><nuxt-link to="/">Home</nuxt-link></h2>
          <h2><nuxt-link to="/blog">Blog</nuxt-link></h2>
          <h2><nuxt-link to="/sobre-mi">Sobre mí</nuxt-link></h2>
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
              src="https://res.cloudinary.com/rserrano/image/upload/v1600717003/blog/roberto-serrano_desarrollador_web_tarragona.jpg"
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
              <nuxt-link to="/sobre-mi">sobre mí</nuxt-link>
              o consultar algunos de mis
              <nuxt-link to="/sobre-mi">proyectos.</nuxt-link>
            </p>
          </h2>
          <Social />
          <ColorMode />
        </div>
      </div>
    </div> -->
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
