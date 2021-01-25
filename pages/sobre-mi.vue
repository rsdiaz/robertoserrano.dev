<template>
  <div>
    <Animation />
    <TopAngle />
    <ResponsiveNav />
    <Header :title="title" :subtitle="subtitle" />
    <section class="container pb-6">
      <div class="about-intro columns">
        <div class="column is-8">
          <p>
            <b>Hola!</b>, soy Roberto Serrano Diaz-Grande, técnico informático y
            desarrollador web. Me apasiona la tecnología en especial la web, la
            programación, los sistemas operativos, los servidores NAS, los
            videojuegos...
          </p>
          <p>
            Navegando en Internet desde los 90, metódico, resolutivo y en
            continua formación, vamos un regalo sin envoltorio xD. No puedo
            estar sin algún proyecto entre manos.
          </p>
          <p>
            Si quieres contactar conmigo y saber más sobre mí, puedes ponerte en
            contacto rellenando el formulario de <a href="#">contacto</a>.
          </p>
        </div>
        <div class="column is-4"></div>
      </div>
    </section>
    <section class="container pt-6">
      <h1 class="subtitle is-3 has-text-centered">🏆 Skills</h1>
      <div class="columns">
        <div class="column is-4">
          <div class="skill">
            <h2 class="subtitle is-4 has-text-centered">Frontend</h2>
            <IconFront />
            <ul class="has-text-centered">
              <li>HTML</li>
              <li>CSS</li>
              <li>JavaScript</li>
              <li>Vue</li>
              <li>NuxtJs</li>
            </ul>
          </div>
        </div>
        <div class="column is-4">
          <div class="skill">
            <h2 class="subtitle is-4 has-text-centered">Backend</h2>
            <IconBackend />
            <ul class="has-text-centered">
              <li>PHP</li>
              <li>NodeJs</li>
              <li>MySQL</li>
              <li>Express</li>
              <li>MongoDB</li>
            </ul>
          </div>
        </div>
        <div class="column is-4">
          <div class="skill">
            <h2 class="subtitle is-4 has-text-centered">Tools</h2>
            <IconCms />
            <ul class="has-text-centered">
              <li>WordPress</li>
              <li>Prestashop</li>
              <li>WooCommerce</li>
              <li>Ghost</li>
              <li>Git</li>
            </ul>
          </div>
        </div>
      </div>
      <!-- <div class="columns content blog-list-wrapper">
        <div class="card column">
          <div class="blog-excerpt">
            <hr />
            <h2 class="title is-3">Contacto</h2>
            <p>
              Puedes ponerte en contacto conmigo rellenando el siguiente
              formulario. En el campo mensaje te agradecería que pusieras todala
              información posible para que mi respuesta sea lo mas acertada
              posible.
            </p>
            <p>O tal vez quieras escribirme a través de Twitter</p>
            <p>
              Escríbeme si estas interesado en mis servicios, si tienes alguna
              duda o simplemente si quieres saludarme.
            </p>
            <p>
              Una vez reciba tu mensaje, no tardare mucho en responderte. 👍
            </p>
            <hr />
            <h2 class="title is-3">Formulario</h2>
            <FormContact />
          </div>
        </div>
      </div> -->
    </section>
    <section class="container pt-6">
      <h1 class="title is-1 has-text-centered">📨</h1>
      <h1 class="subtitle is-3 has-text-centered">
        ¿Quieres ponerte en contacto conmigo?
      </h1>
      <nuxt-link to="/contacto" class="button btn-site">Escríbeme</nuxt-link>
    </section>
    <SocialList />
    <ColorMode />
    <Footer />
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: 'Sobre mí',
      subtitle: 'Roberto Serrano Diaz-Grande',
    }
  },
  head() {
    return {
      title: `Sobre mí | Roberto Serrano Diaz-Grande`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Roberto Serrano Diaz-Grande | Desarrollador Web',
        },
        // Open Graph
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Sobre mí | Roberto Serrano Diaz-Grande',
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'Roberto Serrano Diaz-Grande | Desarrollador Web',
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: 'Sobre mí | Roberto Serrano Diaz-Grande',
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: 'Roberto Serrano Diaz-Grande | Desarrollador Web',
        },
      ],
    }
  },
}
</script>
<style lang="scss">
@import '~/assets/scss/pages/sobre-mi.scss';
</style>
