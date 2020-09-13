<template>
  <div class="section has-text-centered">
    <a :href="getTwitterShareUrl" class="button is-info is-outlined">
      ¿Te gustó este artículo? ¡Compártelo en Twitter!
    </a>
  </div>
</template>
<script>
export default {
  props: {
    article: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      url: 'https://robertoserrano.dev',
      twitter: 'https://twitter.com/share?url=',
      text: '&text=',
      via: '&via=Rovbeat',
    }
  },
  computed: {
    getTwitterShareUrl() {
      const uri =
        this.twitter +
        this.url +
        this.article.path +
        this.text +
        this.article.title +
        this.via
      return encodeURI(uri)
    },
  },
}
</script>
