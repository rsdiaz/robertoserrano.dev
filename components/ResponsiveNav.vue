<template>
  <div class="is-hidden-desktop">
    <div :class="{ close: isOpen }" class="burger" @click="onClick">
      <div class="patty"></div>
      <div class="patty"></div>
      <div class="patty"></div>
    </div>
    <nav :class="{ menu_open: isOpen }" class="menu">
      <ul class="menu_list">
        <li v-for="(link, value) in menuLinks" :key="value">
          <a :href="link.link">{{ link.text }}</a>
        </li>
      </ul>
    </nav>
  </div>
</template>
<script>
export default {
  name: 'Menu',
  data() {
    return {
      isOpen: false,
      menuLinks: {
        home: {
          text: 'Home',
          link: '/',
        },
        blog: {
          text: 'Blog',
          link: '/blog',
        },
        about: {
          text: 'Sobre mí',
          link: '/sobre-mi',
        },
        contact: {
          text: 'Contacto',
          link: '/contacto',
        },
      },
    }
  },
  methods: {
    onClick() {
      this.isOpen = !this.isOpen
    },
  },
}
</script>
<style lang="scss" scoped>
@import '~/assets/scss/components/responsive-nav.scss';
</style>
