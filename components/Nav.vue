<template>
  <div id="navbar" class="columns is-variable pb-3 pt-5 is-hidden-mobile">
    <div class="column is-2">
      <nuxt-link to="/" class="button">
        <IconHome />
        Home
      </nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/blog" class="button">
        <IconBook />
        Blog
      </nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/sobre-mi" class="button">
        <IconUser />
        Sobre mí
      </nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/contacto" class="button">
        <IconAt />
        Contacto
      </nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/contacto" class="button">
        <IconGithub />
        Github
      </nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/contacto" class="button">
        <IconTwitter />
        Twitter
      </nuxt-link>
    </div>
  </div>
</template>

<style lang="scss">
@import '~/assets/scss/components/nav.scss';
</style>
