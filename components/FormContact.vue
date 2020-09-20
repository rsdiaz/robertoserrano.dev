<template>
  <div class="card card-content">
    <form action="https://formspree.io/moqewooe" method="POST">
      <div class="field">
        <label class="label">Nombre</label>
        <div class="control">
          <input
            id="fname"
            v-model="form.nombre"
            class="input"
            :class="{ 'is-success': form.nombre }"
            type="text"
            placeholder="Aquí, tu nombre"
            required
          />
        </div>
        <p v-if="form.nombre" class="help is-success">
          Nombre introducido correctamente
        </p>
        <p v-else class="help is-danger">
          Se necesita un nombre para enviar el formulario
        </p>
      </div>
      <div class="field">
        <label class="label">Email</label>
        <div class="control">
          <input
            v-model="form.email"
            class="input"
            type="email"
            placeholder="Aquí, tu email"
            name="_replyto"
            required
          />
        </div>
        <p v-if="validEmail(form.email)" class="help is-success">
          El email es valido...
        </p>
        <p v-else class="help is-danger">
          Se necesita un email para enviar el formulario
        </p>
      </div>
      <div class="field">
        <label class="label">Mensaje</label>
        <div class="control">
          <textarea
            v-model="form.mensaje"
            class="textarea"
            placeholder="Mensaje"
            name="message"
            required
          >
          </textarea>
          <p v-if="!form.mensaje" class="help is-danger">
            Necesito un mesaje para responderte.
          </p>
        </div>
      </div>
      <div class="control">
        <button class="button is-link" :disabled="false">Enviar</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        nombre: null,
        email: null,
        mensaje: null,
        valid: false,
      },
    }
  },
  methods: {
    /* checkForm() {
      console.log(this.form.nombre)
    }, */
    validEmail: (email) => {
      // eslint-disable-next-line no-useless-escape
      const regex = /^([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})+$/
      return regex.test(email)
    },
  },
}
</script>
