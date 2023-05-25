<template>
  <div class="q-pa-xl">
    <q-form @submit="salvar" class="q-gutter-y-md">
      <div class="q-mb-md text-center text-h6">Formulário Pessoa</div>
      <q-input label="" v-model="nome" />
      <q-input label="" v-model="sobrenome" />
      <q-input
        label="cep"
        v-model="cep"
        mask="#####-###"
        unmasked-value
      ></q-input>

      <componente-endereco @update="updateForm($event)" :cep="cep" />
      <q-btn type="submit"></q-btn>
    </q-form>
  </div>
</template>

<script setup>
import ComponenteEndereco from "src/components/ComponenteEndereco.vue";
import { ref } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();
const endereco = ref({});
function salvar(payload) {
  // logica submit
  router.push("/cadastro-finalizado");
}
function updateForm(payload) {
  console.log("console pai", payload);
  endereco.value = payload;
}
const nome = ref("");
const sobrenome = ref("");
const cep = ref("");
</script>
