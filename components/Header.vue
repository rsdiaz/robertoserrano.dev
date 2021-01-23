<template>
  <header>
    <div class="container">
      <Nav />
      <div>
        <h1 class="title">{{ title }}</h1>
        <h2 class="subtitle is-3">Roberto Serrano Diaz-Grande</h2>
        <div class="border-bottom"></div>
        <div class="about-intro columns">
          <div class="column is-8"></div>
          <div class="column is-4"></div>
        </div>
      </div>
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
