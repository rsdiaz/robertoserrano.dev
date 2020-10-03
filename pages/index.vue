<template>
  <div id="particles-js">
    <div id="top-angle"></div>
    <header>
      <div class="container">
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
          <div class="columns is-variable pb-3 pt-5">
            <div class="column is-2">
              <nuxt-link to="/contacto" class="button">Contacto</nuxt-link>
            </div>
            <div class="column is-2">
              <nuxt-link to="/sobre-mi" class="button">Sobre mí</nuxt-link>
            </div>
            <div class="column is-2">
              <nuxt-link to="/blog" class="button">Blog</nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </header>
    <section>
      <div class="container">
        <div class="columns is-variable is-8">
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
            >
              <span :style="[!index ? { display: 'inline-block' } : {}]">
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
    const articles = await $content('/blog').without(['body', 'toc']).fetch()
    return { articles }
  },
  mounted() {
    // eslint-disable-next-line no-undef
    particlesJS('particles-js', {
      particles: {
        number: {
          value: 33,
          density: {
            enable: true,
            value_area: 1420.4657549380909,
          },
        },
        color: {
          value: '#ffffff',
        },
        shape: {
          type: 'star',
          stroke: {
            width: 0,
            color: '#000000',
          },
          polygon: {
            nb_sides: 5,
          },
          image: {
            src: 'img/github.svg',
            width: 100,
            height: 100,
          },
        },
        opacity: {
          value: 0.06313181133058181,
          random: false,
          anim: {
            enable: false,
            speed: 1,
            opacity_min: 0.1,
            sync: false,
          },
        },
        size: {
          value: 5,
          random: true,
          anim: {
            enable: false,
            speed: 40,
            size_min: 0.1,
            sync: false,
          },
        },
        line_linked: {
          enable: true,
          distance: 150,
          color: '#ffffff',
          opacity: 0.4,
          width: 1,
        },
        move: {
          enable: true,
          speed: 6,
          direction: 'none',
          random: false,
          straight: false,
          out_mode: 'out',
          bounce: false,
          attract: {
            enable: false,
            rotateX: 600,
            rotateY: 1200,
          },
        },
      },
      interactivity: {
        detect_on: 'canvas',
        events: {
          onhover: {
            enable: false,
            mode: 'repulse',
          },
          onclick: {
            enable: false,
            mode: 'push',
          },
          resize: true,
        },
        modes: {
          grab: {
            distance: 400,
            line_linked: {
              opacity: 1,
            },
          },
          bubble: {
            distance: 400,
            size: 40,
            duration: 2,
            opacity: 8,
            speed: 3,
          },
          repulse: {
            distance: 200,
            duration: 0.4,
          },
          push: {
            particles_nb: 4,
          },
          remove: {
            particles_nb: 2,
          },
        },
      },
      retina_detect: true,
    })
  },
  head() {
    return {
      script: [
        {
          src:
            'https://cdnjs.cloudflare.com/ajax/libs/particles.js/2.0.0/particles.min.js',
        },
      ],
      title:
        '🙋‍♂️ Roberto Serrano | 💻 Desarrollador Web en Tarragona | 🌍 robertoserrano.dev',
    }
  },
}
</script>
