<template>
  <div>
    <Animation />
    <TopAngle />
    <ResponsiveNav />
    <Nav />
    <Nuxt />
    <SocialList />
    <Footer />
  </div>
</template>

<script>
import Animation from '@/components/Animation'
import TopAngle from '@/components/TopAngle'
import ResponsiveNav from '@/components/ResponsiveNav'
import Nav from '@/components/Nav'
import SocialList from '@/components/SocialList'
import Footer from '@/components/Footer'

export default {
  components: {
    Animation,
    TopAngle,
    ResponsiveNav,
    Nav,
    SocialList,
    Footer,
  },
  head() {
    return {
      htmlAttrs: { lang: 'es' },
    }
  },
}
</script>
