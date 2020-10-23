<template>
  <div class="columns is-variable pb-3 pt-5">
    <div class="column is-2">
      <nuxt-link to="/" class="button">Home</nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/blog" class="button">Blog</nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/sobre-mi" class="button">Sobre mí</nuxt-link>
    </div>
    <div class="column is-2">
      <nuxt-link to="/contacto" class="button">Contacto</nuxt-link>
    </div>
  </div>
</template>

<style lang="scss">
@import '~/assets/scss/components/nav.scss';
</style>
