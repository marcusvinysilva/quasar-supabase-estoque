<template>
  <q-page padding>
    <q-form class="row justify-center" @submit.prevent="handleLogin">
    <p class="col-12 text-h5 text-center"> Login </p>
    <div class="col-md-4 col-sm-6 col-xs-10 q-gutter-y-md">
      <q-input
        label="Email"
        v-model="form.email"
      />

      <q-input
        label="Senha"
        v-model="form.password"
      />

      <div class="full-width q-pt-md">
        <q-btn
          label="Login"
          color="primary"
          class="full-width"
          outline
          rounded
          type="submit"
        />
      </div>

      <div class="full-width">
        <q-btn
          label="Cadastrar"
          color="primary"
          class="full-width"
          flat
          to="/register"
        />
      </div>
    </div>
  </q-form>
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useRouter } from 'vue-router'
import useAuthUser from 'src/composables/UseAuthUser'

export default defineComponent({
  name: 'LoginPage',

  setup () {
    const router = useRouter()

    const { login } = useAuthUser()

    const form = ref({
      email: '',
      password: ''
    })

    const handleLogin = async () => {
      try {
        await login(form.value)
        router.push({ name: 'me' })
      } catch (error) {
        alert(error.message)
      }
    }

    return {
      form,
      handleLogin
    }
  }
})
</script>
