<template>
  <q-page padding>
    <p class="text-body1">
      Obrigado por se cadastrar!
    </p>
    <p class="text-body1">
      Por favor, confirme seu email para finalizar o seu cadastro: <strong>{{ $route.query.email }}</strong>
    </p>

  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'EmailConfirmationPage'
})
</script>
