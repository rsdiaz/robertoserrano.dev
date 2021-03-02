<template>
  <div class="container">
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
  </div>
</template>

<script>
import IconHome from '~/components/global/icons/IconHome'
import IconBook from '~/components/global/icons/IconBook'
import IconUser from '~/components/global/icons/IconUser'
import IconAt from '~/components/global/icons/IconAt'
import IconGithub from '~/components/global/icons/IconGithub'
import IconTwitter from '~/components/global/icons/IconTwitter'

export default {
  components: {
    IconHome,
    IconBook,
    IconUser,
    IconAt,
    IconGithub,
    IconTwitter,
  },
}
</script>

<style lang="scss">
@import '~/assets/scss/components/nav.scss';
</style>
