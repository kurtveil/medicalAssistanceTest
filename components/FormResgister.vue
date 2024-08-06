<template>
    <UForm :schema="schema" :state="state" class="space-y-4" @submit="onSubmit">
    <div class="w-100">
    
      <UFormGroup  name="celphone">
        <UInput   class=" bg-white" placeholder="Celular" v-model="state.celphone" type="text" />
      </UFormGroup>
      <UFormGroup  name="nombre">
        <UInput   class=" bg-white" placeholder="Nombre" v-model="state.name" type="text" />
      </UFormGroup>
      <UFormGroup  name="apellidos">
        <UInput   class=" bg-white" placeholder="Apellidos" v-model="state.surname" type="text" />
      </UFormGroup>
      <UFormGroup  name="correo-electronico">
        <UInput   class=" bg-white" placeholder="Corre electronico" v-model="state.email" type="text" />
      </UFormGroup>
    </div>
    <div class="p-6 flex items-center justify-center">
      <div>
        <button type="submit" class=" bg-yellow-500 hover:bg-yellow-700 text-white font-bold py-2 px-4 ">
          Ingresar
        </button>
      </div>

    </div>
  </UForm>
</template>

<script setup lang="ts">
import { defineEmits } from 'vue';

// const props = defineProps({
//   modelValue: String, // Ajusta el tipo según tus datos reales
// });

const emit = defineEmits(['update:modelValue']);
import { object, string, type InferType } from 'yup'
import type { FormSubmitEvent } from '#ui/types'
// import { ref, computed, defineProps } from 'vue';
import { reactive } from 'vue';
const token = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIzIiwianRpIjoiZThiNzhmNDIyZjg0OTUzNjlmNGU5MDJlMjUzMmIwNmUzYTQyY2QxNTg0OTkxMGVmNzJlYTY2MTc3Y2MyZTE1NWZhZjUyYjc2MTk5ZThlNWUiLCJpYXQiOjE3MjA2NTE0MzAuNTkzMzM1LCJuYmYiOjE3MjA2NTE0MzAuNTkzMzQxLCJleHAiOjE3NTIxODc0MzAuNTY2NjcsInN1YiI6IjE1Iiwic2NvcGVzIjpbXX0.w-KFa5vyn617vrlsOCeVLtWsNlAz52qeEQerr328x16dMRYaiYkUolQOYshi43cjGftCGUFFx9gWll_8Nds1Av_lgkVXBBz37nPUqdYp2lI_pMmNabYAZDr44m8_mQeMHSSxulwSL1Z1QfWQa_-lHYVidfeWF4SoZYC9UFAxZEtSg724tGV9CFXyOVoyCZAnSGtPE17iC4uBMtwlAjXxRs94-BHXkUeaNVvEeBXCE2BZXjLPsVdiSb0xFAIAgc2Bo0XG7Y1PmAA-awWMrY0HZzb0tLE7Zi33tIsVexDX9qkEcnoEaMziyaWkeXIy_iJo-FNUXMZ0DVT6Ky5Wa5-gzzsy6I4HgthVW-ys5dXZtf8XE3gjZx5R95vXKwWYgDcUX9aBpB2qKoxGLaL3Ccx3zbuJlEmSZCKmwuO-OJ_6Ducej6FBHJ3QPx9eeKMkixxPaGJ39YQPmEy5n3cTJhFvj1rHFfrJIrtLOYtC6-1w2xRbfmKbBqezVA0anKAU2EMW_B-nXtAT4ATvySYV-YOlkzSc4qgE-l_mhPujfqI9TcQP-37oBs0KY00OSJX-n7B2185x81tk9ZeBAS4TrqFZtT_GEdQkcmlkbcy08sEJYV-oKKzyub3UGNjYHkXU21HM0yndBUZ3D6KwV5sYU9GdpeLjM-ON6VqN6vpEkg1NKmo';
const schema = object({
    celphone: string()
    .min(8, 'Must be at least 8 characters')
    .required('Required'),
    name:  string().required('Required'),
    surname:  string().required('Required'),
    email:  string().required('Required')
})
type Schema = InferType<typeof schema>
const state = reactive({
  celphone: undefined,
  name: undefined,
  surname: undefined,
  email: undefined,
})
async function onSubmit(event: FormSubmitEvent<Schema>) {
    if (!event.data.document) {
    alert('Por favor, completa los campos campo.');
    return;
  }
  
}




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
