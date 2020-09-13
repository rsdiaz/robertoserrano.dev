<template>
  <section class="section description">
    <div class="container post-description">{{ article.description }}</div>
  </section>
</template>
<script>
export default {
  props: {
    article: {
      type: Object,
      required: true,
    },
  },
}
</script>
<style lang="scss" scoped>
section.description {
  padding: 2rem 1.5rem;
  padding-bottom: 0;
  .post-description {
    font-size: 2rem;
  }
}
</style>
