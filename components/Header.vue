<template>
  <header>
    <div class="container">
      <div class="columns is-multiline is-mobile">
        <div class="column is-full-mobile is-four-fifths-desktop">
          <h1 class="title">{{ title }}</h1>
        </div>
        <div class="column">
          <ColorMode />
        </div>
      </div>
      <h2 class="subtitle is-3">{{ subtitle }}</h2>
      <div class="border-bottom"></div>
    </div>
  </header>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      required: true,
    },
  },
}
</script>
<style lang="scss">
@import '~/assets/scss/components/header.scss';
</style>
