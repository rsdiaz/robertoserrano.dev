<template>
  <div>
    <Header :title="title" :subtitle="subtitle" />
    <section class="container pb-6">
      <div class="about-intro columns is-flex-touch">
        <picture class="is-hidden-desktop">
          <img
            src="https://res.cloudinary.com/rserrano/image/upload/v1611353909/blog/Sin_nombre_brvzig.jpg"
            alt=""
          />
        </picture>
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
        <div class="column is-4 is-hidden-touch"></div>
      </div>
    </section>
    <section class="container pt-6">
      <h1 class="title is-1 has-text-centered">📨</h1>
      <h1 class="subtitle is-3 has-text-centered">
        ¿Quieres ponerte en contacto conmigo?
      </h1>
      <nuxt-link to="/contacto" class="button btn-site">Escríbeme</nuxt-link>
    </section>
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
      title: `Roberto Serrano Diaz-Grande | ${this.title}`,
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
