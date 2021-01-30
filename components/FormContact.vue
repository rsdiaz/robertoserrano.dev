<template>
  <form method="POST" novalidate="true" @submit="checkForm">
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
      <p
        v-if="form.errors.nameError || form.nombre == null"
        class="help is-error"
      >
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
      <p v-if="form.errors.emailError && form.email == 0" class="help is-error">
        Se necesita un email valido para que te pueda responder.
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
        <p
          v-if="form.errors.msgError && form.mensaje == 0"
          class="help is-error"
        >
          Necesito un mensaje para responderte.
        </p>
      </div>
    </div>
    <div class="control">
      <input type="submit" class="button is-link" value="Enviar" />
    </div>
  </form>
</template>

<script>
import { required, minLength, email } from 'vuelidate/lib/validators'

export default {
  data() {
    return {
      form: {
        nombre: null,
        email: null,
        mensaje: null,
      },
    }
  },
  methods: {
    checkForm(e) {
      if (!this.form.nombre) {
        this.form.errors.nameError = true
      } else {
        this.form.errors.nameError = false
      }

      if (!this.form.email) {
        this.form.errors.emailError = true
      } else if (!this.validEmail(this.form.email)) {
        this.form.errors.emailError = true
      }

      if (!this.form.mensaje) {
        this.form.errors.msgError = true
      }

      e.preventDefault()
    },
    validEmail: (email) => {
      // eslint-disable-next-line no-useless-escape
      const regex = /^([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})+$/
      return regex.test(email)
    },
  },
}
</script>
