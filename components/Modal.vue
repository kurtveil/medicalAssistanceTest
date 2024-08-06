<template>
    <div class="fixed inset-0 flex items-center justify-center z-50">
        <div class=" bg-white rounded-lg shadow-lg">
            <div class="  m-5">
                <img src="../assets/imgs/doctorone.png" alt="">
            </div>
            <div class="modal-container p-8 ">

                <div v-if="datosDesdeHijo.name" class="flex  items-center justify-center">
                    <h3 class="text-xl font-bold m-3"> Hola {{ datosDesdeHijo.name }}</h3>
                </div>
                <div class="flex  items-center justify-center">
                    <img src="../assets/imgs/doc.png" class="w-40 m-5" alt="doc">
                </div>
                <div v-if="!datosDesdeHijo.name" class="flex justify-center ">
                    <h2 class="text-xl font-bold m-3">Asistencia Médica Virtual Inmediata</h2>
                </div>
                <div v-if="!datosDesdeHijo.name && !datosDesdeHijo.message" class="flex justify-center m-3">
                    <Form v-model="datosDesdeHijo" />
                </div>
                <div v-if="datosDesdeHijo.message" class="flex justify-center m-3">
                    <FormRegister  />
                </div>
    
                <div v-if="datosDesdeHijo.name" >
                    <div class="flex justify-center">
                       <h3 class="text-xl font-bold m-3"> Tú médico te está esperando </h3>
                    </div>
                    <div class="p-6 flex items-center justify-center">
                        <div>
                            <button type="button"
                                class=" bg-yellow-500 hover:bg-yellow-700 text-white font-bold py-2 px-4 ">
                                Conectar
                            </button>
                        </div>
    
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const datosDesdeHijo = ref('');
import Form from './Form.vue';
import FormRegister from './FormResgister.vue';


</script>
<style>
@import url("/assets/styles.css");
</style>