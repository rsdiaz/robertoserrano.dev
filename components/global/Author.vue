<template>
  <div class="card author-card">
    <div class="card-content">
      <div class="media">
        <div class="media-left">
          <figure class="image is-64x64">
            <img
              :src="author.img"
              alt="Roberto Serrano desarrollo web Tarragona"
            />
          </figure>
        </div>
        <div class="media-content">
          <h3 class="title is-5">{{ author.name }}</h3>
          <p class="subtitle is-6">
            <a href="https://twitter.com/Rovbeat">@Rovbeat</a>
          </p>
        </div>
      </div>
      <div class="content">
        <p>{{ author.bio }}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    author: {
      type: Object,
      required: true,
    },
  },
}
</script>
<style lang="scss" scoped>
.author-card {
  @include tablet {
    margin-left: 1rem;
    margin-right: 1rem;
  }
}
</style>
