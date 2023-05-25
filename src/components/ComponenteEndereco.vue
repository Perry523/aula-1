<template>
  <div>
        <!--> teste <-->
    <div class="row">
        <!--> teste <-->
        <q-input v-model="teste" label="rua"></q-input>
      <q-input label="número"></q-input>
      <q-input label="número"></q-input>
        <!--> teste <-->
      <q-input label="complemento"></q-input>
    </div>
  </div>
</template>
<script setup>
import { watch, ref } from "vue";
import axios from "axios";
const teste = ref("");
const props = defineProps({
  cep: {
    type: String,
    required: true,
    default: "",
  },
});
const emit = defineEmits(["update"]);
watch(props, async (value) => {
  if (props.cep.length === 8) {
    const { data } = await axios.get(
      `https://viacep.com.br/ws/${props.cep}/json/`
    );
    rua.value = data.logradouro;
    emit("update", data);
  }
});
</script>
