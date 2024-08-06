<template>
  <form @submit.prevent="submitForm">
    <div class="w-100">

      <input v-model="textInput" @input="$emit('input', $event.target.value)" class="numeric-input bg-white" type="text"
        placeholder="Número de identificación" />
      <div v-if="!campoValido" role="alert">

        <div class="border border-t-0 border-red-400 rounded-b bg-red-100 px-4 py-3 text-red-700">
          <p>Ingrese un número de documento.</p>
        </div>
      </div>
    </div>
    <div class="p-6 flex items-center justify-center">
      <div>
        <button type="submit" class="mt-2 bg-yellow-500 hover:bg-yellow-700 text-white font-bold py-2 px-4 ">
          Ingresar
        </button>
      </div>

    </div>
  </form>
</template>

<script setup>
import { ref, computed, defineProps } from 'vue';
const textInput = ref('');
const campoValido = computed(() => textInput.value.trim() !== '');
const token = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIzIiwianRpIjoiZThiNzhmNDIyZjg0OTUzNjlmNGU5MDJlMjUzMmIwNmUzYTQyY2QxNTg0OTkxMGVmNzJlYTY2MTc3Y2MyZTE1NWZhZjUyYjc2MTk5ZThlNWUiLCJpYXQiOjE3MjA2NTE0MzAuNTkzMzM1LCJuYmYiOjE3MjA2NTE0MzAuNTkzMzQxLCJleHAiOjE3NTIxODc0MzAuNTY2NjcsInN1YiI6IjE1Iiwic2NvcGVzIjpbXX0.w-KFa5vyn617vrlsOCeVLtWsNlAz52qeEQerr328x16dMRYaiYkUolQOYshi43cjGftCGUFFx9gWll_8Nds1Av_lgkVXBBz37nPUqdYp2lI_pMmNabYAZDr44m8_mQeMHSSxulwSL1Z1QfWQa_-lHYVidfeWF4SoZYC9UFAxZEtSg724tGV9CFXyOVoyCZAnSGtPE17iC4uBMtwlAjXxRs94-BHXkUeaNVvEeBXCE2BZXjLPsVdiSb0xFAIAgc2Bo0XG7Y1PmAA-awWMrY0HZzb0tLE7Zi33tIsVexDX9qkEcnoEaMziyaWkeXIy_iJo-FNUXMZ0DVT6Ky5Wa5-gzzsy6I4HgthVW-ys5dXZtf8XE3gjZx5R95vXKwWYgDcUX9aBpB2qKoxGLaL3Ccx3zbuJlEmSZCKmwuO-OJ_6Ducej6FBHJ3QPx9eeKMkixxPaGJ39YQPmEy5n3cTJhFvj1rHFfrJIrtLOYtC6-1w2xRbfmKbBqezVA0anKAU2EMW_B-nXtAT4ATvySYV-YOlkzSc4qgE-l_mhPujfqI9TcQP-37oBs0KY00OSJX-n7B2185x81tk9ZeBAS4TrqFZtT_GEdQkcmlkbcy08sEJYV-oKKzyub3UGNjYHkXU21HM0yndBUZ3D6KwV5sYU9GdpeLjM-ON6VqN6vpEkg1NKmo';
const submitForm = () => {
  if (!campoValido.value) {
    alert('Por favor, completa el campo.');
    return;
  }
  $fetch(`https://pttest.doctorone.com/api/auth/get_data_client?numberId=${textInput.value}`, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      Authorization: `Bearer ${token}`,
    }
  }).then((res) => {
  })
  const props = defineProps({
    res
  });


}



watch(() => textInput, (nuevoValor) => {
  if (!nuevoValor.trim()) {
    // El campo está vacío, muestra un mensaje de advertencia
    console.log('Campo vacío');
  } else {
    // El campo tiene datos, realiza alguna acción adicional si es necesario
    console.log('Campo con datos:', nuevoValor);
  }
});

</script>

<style scoped>
.numeric-input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
}

.alert-message {
  color: red;
}

.hidden {
  display: none;
}
</style>
