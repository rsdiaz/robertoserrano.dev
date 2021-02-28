<template>
  <div>
    <article
      v-for="(article, index) in articles"
      :key="index"
      class="post-list"
    >
      <p class="date is-size-7">{{ formatDate(article.createdAt) }}</p>
      <h2 class="title is-4">
        <div
          :style="[
            !index
              ? {
                  display: 'flex',
                  flexDirection: 'row',
                  flexWrap: 'wrap-reverse',
                }
              : {},
          ]"
        >
          <NuxtLink :to="`/blog/${article.slug}`">
            {{ article.title }}
          </NuxtLink>
          <span v-if="!index" class="tag">NUEVO</span>
        </div>
      </h2>
      <p>{{ article.description }}</p>
      <strong>
        <NuxtLink :to="`/blog/${article.slug}`"> Leer más</NuxtLink>
      </strong>
    </article>
  </div>
</template>

<script>
export default {
  props: {
    articles: {
      type: Array,
      required: true,
    },
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
  },
}
</script>
