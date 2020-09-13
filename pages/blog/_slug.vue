<template>
  <div>
    <div class="card section blog-page">
      <article>
        <header>
          <div class="title-container mb-4">
            <div
              id="blog-post-cover"
              class="background-cover"
              :style="{ backgroundImage: 'url(' + article.picture + ')' }"
            >
              <div class="background-shroud">
                <p class="title has-text-centered is-2">
                  {{ article.title }}
                </p>
                <p class="date has-text-centered has-text-weight-light">
                  Publicado el {{ formatDate(article.updatedAt) }}
                </p>
              </div>
            </div>
          </div>
        </header>
        <!-- <img class="image" :src="article.picture" :alt="article.alt" /> -->
        <div class="blog-content">
          <BlogDescription :article="article" />
          <section class="section content">
            <hr />
            <!-- markdown content -->
            <nuxt-content :document="article" />
            <hr />
            <TwitterShare :article="article" />
            <Comments />
            <!-- content author component -->
            <Author :author="article.author" />
          </section>
        </div>
      </article>
    </div>
    <Footer />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('blog', params.slug).fetch()
    return { article }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
  },
  head() {
    return {
      title: `${this.article.title} | robertoserrano.dev`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.article.description,
        },
        // Open Graph
        {
          hid: 'og:title',
          property: 'og:title',
          content: this.article.title,
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.article.description,
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.article.title,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.article.description,
        },
      ],
    }
  },
}
</script>
<style lang="scss" scoped>
.section.blog-page {
  max-width: 960px;
  margin: 0 auto;
  padding: 1.5rem 1.5rem;
  background: $white;
}
.title-container,
.background-cover {
  height: calc(100vh - 77px);
}
.background-cover {
  background-position: center center;
  background-size: cover;
  background-repeat: no-repeat;
  transition: 0s linear;
  transition-property: all;
  transition-property: background-position;
}
.background-shroud {
  background: linear-gradient(
    to top,
    rgba(17, 17, 17, 0.8),
    rgba(17, 17, 17, 0.5),
    transparent,
    transparent
  );
  height: calc(100vh - 77px);
  position: relative;
  transition: all 0.4s ease-in-out;
  p.title {
    text-align: center;
    color: #fbfbfb;
    font-size: 4vw;
    text-shadow: 2px 2px 2px #111;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 15%;
    max-width: 80%;
    margin: auto;
  }
  p.date {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    margin-bottom: 58px;
    color: $white-ter;
  }
}

section.content {
  padding: 0 1.5rem;
}

.card.author-card {
  margin: 0;
}

.nuxt-content {
  h2,
  h3,
  h4 {
    font-weight: bold;
    margin-top: 0.5rem;
    margin-bottom: 1.25rem;
    line-height: 1.25;
  }
  p {
    margin-bottom: 1.563rem;
    font-size: 1.125rem;
    line-height: 1.833em;
  }
}
.nuxt-content h2 {
  font-size: 1.875rem;
}
.nuxt-content h3 {
  font-size: 1.5rem;
}

.nuxt-content-highlight {
  margin: 1.2rem 0;
}
</style>
