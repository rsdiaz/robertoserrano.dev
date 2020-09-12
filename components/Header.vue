<template>
  <nav
    class="navbar"
    :class="[isHome() ? 'is-light' : 'is-primary is-hidden-desktop']"
    role="navigation"
    aria-label="main navigation"
  >
    <div class="navbar-brand">
      <nuxt-link to="/" :class="'navbar-item'">
        <Logo />
        <h3 class="ml-2 has-text-weight-bold is-hidden-mobile">
          robertoserrano.dev
        </h3>
      </nuxt-link>
      <a
        role="button"
        class="navbar-burger burger"
        aria-label="menu"
        aria-expanded="false"
        data-target="navbarBasicExample"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>
    <transition name="fade">
      <div id="navbarBasicExample" class="navbar-menu">
        <div class="navbar-start">
          <nuxt-link to="/" :class="'navbar-item tg-menu'">Home</nuxt-link>
          <nuxt-link to="/blog" :class="'navbar-item tg-menu'">Blog</nuxt-link>
          <nuxt-link to="/blog" :class="'navbar-item tg-menu'">
            Sobre mí
          </nuxt-link>
          <nuxt-link to="/blog" :class="'navbar-item tg-menu'">
            Contacto
          </nuxt-link>
        </div>

        <div class="navbar-end">
          <div class="navbar-item">
            <!-- <div class="buttons">
              <a class="button is-primary">
                <strong>Sign up</strong>
              </a>
              <a class="button is-light">Log in</a>
            </div> -->
          </div>
        </div>
      </div>
    </transition>
  </nav>
</template>
<script>
export default {
  mounted: () => {
    const $navbarBurgers = Array.prototype.slice.call(
      document.querySelectorAll('.navbar-burger'),
      0
    )
    const navbarItems = document.querySelectorAll('.tg-menu')

    if ($navbarBurgers.length > 0) {
      $navbarBurgers.forEach((el) => {
        el.addEventListener('click', () => {
          const target = el.dataset.target
          const $target = document.getElementById(target)
          el.classList.toggle('is-active')
          $target.classList.toggle('is-active')
        })
      })
      navbarItems.forEach((element) => {
        element.addEventListener('click', () => {
          const target = $navbarBurgers[0].dataset.target
          const $target = document.getElementById(target)
          $navbarBurgers[0].classList.toggle('is-active')
          $target.classList.remove('is-active')
        })
      })
    }
  },
  methods: {
    isHome() {
      // eslint-disable-next-line
      return this.$route.name !== 'index'
    },
  },
}
</script>
