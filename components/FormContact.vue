<template>
  <form id="form" name="form" novalidate="true" @submit.prevent="checkForm">
    <div class="field">
      <label class="label">Nombre</label>
      <div class="control">
        <input
          id="fname"
          v-model="form.name"
          :class="{
            'is-success':
              (submit && !$v.form.name.required) || !$v.form.name.minLength,
          }"
          type="text"
          placeholder="Aquí, tu nombre"
        />
      </div>
      <p v-if="submit && !$v.form.name.required" class="help is-danger">
        Se necesita un nombre para enviar el formulario
      </p>
      <p v-if="submit && !$v.form.name.minLength" class="help is-danger">
        El campo nombre debe tener al menos 2 caracteres
      </p>
    </div>
    <div class="field">
      <label class="label">Email</label>
      <div class="control">
        <input
          v-model="form.email"
          type="email"
          placeholder="Aquí, tu email"
          name="_replyto"
        />
      </div>
      <p v-if="submit && !$v.form.email.required" class="help is-danger">
        Se necesita un email para enviar el formulario
      </p>
      <p v-if="submit && !$v.form.email.email" class="help is-danger">
        Se necesita un email valido para enviar el formulario
      </p>
    </div>
    <div class="field">
      <label class="label">Mensaje</label>
      <div class="control">
        <textarea v-model="form.message" placeholder="Mensaje" name="message">
        </textarea>
        <p v-if="submit && !$v.form.message.required" class="help is-danger">
          Se necesita un mensaje para enviar el formulario
        </p>
        <p v-if="submit && !$v.form.message.minLength" class="help is-danger">
          El campo mensaje debe tener al menos 2 caracteres
        </p>
      </div>
    </div>
    <div class="field">
      <div class="control">
        <label>
          <input v-model="form.agree" type="checkbox" />
          He leído y acepto la <a href="#">Política de Privacidad</a>
        </label>
      </div>
      <p v-if="submit && !$v.form.agree.required" class="help is-danger">
        Necesitas aceptar la Política de Privacidad
      </p>
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
      submit: false,
      form: {
        name: null,
        email: null,
        message: null,
        agree: null,
      },
    }
  },
  methods: {
    checkForm() {
      this.submit = true
      if (this.$v.$invalid) {
        return false
      }
    },
  },
  validations: {
    form: {
      name: {
        required,
        minLength: minLength(2),
      },
      email: {
        required,
        email,
      },
      agree: {
        required,
      },
      message: {
        required,
        minLength: minLength(2),
      },
    },
  },
}
</script>
