<template>
  <div>
    <Header :title="title" :subtitle="subtitle" />
    <section class="container pb-6">
      <p>
        Puedes ponerte en contacto conmigo rellenando el siguiente formulario.
        En el campo mensaje te agradecería que pusieras toda la información
        posible para que mi respuesta sea lo mas acertada posible.
      </p>
      <p>
        Escríbeme si estas interesado en mis servicios, si tienes alguna duda o
        simplemente si quieres saludarme. Una vez reciba tu mensaje, no tardare
        mucho en responderte. 👍
      </p>
    </section>
    <section class="container form-container">
      <div class="columns">
        <div class="column is-6 card">
          <h2 class="subtitle is-3 has-text-centered">
            Formulario de contacto
          </h2>
          <FormContact />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: 'Contacto',
      subtitle: 'Pagina de contacto',
    }
  },
  head() {
    return {
      title: `Roberto Serrano Diaz-Grande | ${this.title}`,
    }
  },
}
</script>

<style lang="scss">
.form-container {
  div.columns {
    justify-content: center;
  }
  div.card {
    background: var(--bg-fix);
    padding: 38px;
    border-radius: 12px;
  }
  input[type='text'],
  input[type='email'],
  textarea {
    width: 100%;
    border-radius: 2px;
    border: none;
    padding: 12px;
  }
  .label {
    color: var(--link-color);
  }
}
</style>
