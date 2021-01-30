<template>
  <div>
    <Animation />
    <TopAngle />
    <ResponsiveNav />
    <Header :title="title" :subtitle="subtitle" />
    <section class="container pb-6">
      <p>
        Puedes ponerte en contacto conmigo rellenando el siguiente formulario.
        En el campo mensaje te agradecería que pusieras toda la información
        posible para que mi respuesta sea lo mas acertada posible.
      </p>
      <p>O tal vez quieras escribirme a través de Twitter</p>
      <p>
        Escríbeme si estas interesado en mis servicios, si tienes alguna duda o
        simplemente si quieres saludarme.
      </p>
      <p>Una vez reciba tu mensaje, no tardare mucho en responderte. 👍</p>
    </section>
    <section class="container form-container">
      <div class="columns">
        <div class="column is-6">
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
}
</script>

<style lang="scss">
.form-container {
  div.columns {
    justify-content: center;
  }
  input[type='text'],
  input[type='email'] {
    width: 100%;
    border-radius: 0;
    border: none;
    padding: 12px;
    margin-bottom: 18px;
  }
  textarea {
    width: 100%;
    padding: 12px;
    margin-bottom: 18px;
  }
  .is-error {
    padding: 12px;
    background: #202020;
    color: var(--link-color);
  }
  .label {
    display: block;
    margin: 5px 0;
    font-weight: 900;
    color: var(--link-color);
  }
}
</style>
