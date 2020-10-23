<template>
  <div>
    <Animation />
    <TopAngle />
    <header>
      <div class="container">
        <Nav />
        <div>
          <h1 class="title">Roberto Serrano Diaz-Grande</h1>
          <h2 class="subtitle is-3">Desarrollador Web | Tarragona</h2>
          <p>
            Desde 2012, llevo desarrollando aplicaciones web y he ayudado a
            muchas personas a lograr cosas innovadoras en la Web. Principalmente
            trabajo con herramientas y frameworks modernos como Wordpress,
            VueJs, Angular...
          </p>
          <p>
            Comparto mi aprendizaje y conocimiento a traves de mi
            <nuxt-link to="/blog">blog</nuxt-link>, en el cual publico artículos
            sobre desarrollo web y mi día a día tecnológico.
          </p>
          <p>
            Cuando no estoy codificando o presionando píxeles, me encontrarás en
            el gimnasio, jugando al fútbol o anotando más de par en el campo de
            golf.
          </p>
        </div>
      </div>
    </header>
    <section>
      <div class="container">
        <div class="columns is-variable is-2-mobile is-0-tablet is-3-desktop">
          <div class="column frontend">
            <h2 class="is-size-3 has-text-weight-bold mb-3">Frontend</h2>
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
            <h2 class="is-size-3 has-text-weight-bold mb-3">Backend</h2>
            <ul>
              <li>
                <a href="">
                  node-clima
                  <span>Modulo NodeJs escrito en TypeScript</span>
                </a>
                <a href="">
                  WebSat
                  <span>
                    Sistema de gestión Web para servicio técnico informático,
                    con NodeJs, Express, Handlebars y MySQL
                  </span>
                </a>
              </li>
            </ul>
          </div>
          <div class="column article">
            <h2 class="is-size-3 has-text-weight-bold mb-3">Artículos</h2>
            <a
              v-for="(article, index) in articles"
              :key="index"
              :href="`/blog/${article.slug}`"
              :style="[!index ? { display: 'flex' } : {}]"
            >
              <span>
                {{ article.title }}
              </span>
              <span v-if="!index" class="tag">NUEVO</span>
            </a>
          </div>
        </div>
      </div>
    </section>
    <SocialList />
    <ColorMode />
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
  head() {
    return {
      title:
        '🙋‍♂️ Roberto Serrano | 💻 Desarrollador Web en Tarragona | 🌍 robertoserrano.dev',
    }
  },
}
</script>
