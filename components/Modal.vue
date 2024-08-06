<template>
    <div class="fixed inset-0 flex items-center justify-center z-50">
        <div class="modal-container bg-white rounded-lg shadow-lg">
            <div class="  m-3">
               <img src="../assets/imgs/doctorone.png" alt="">
            </div>
            <div class="flex  items-center justify-center">
               <img src="../assets/imgs/doc.png" class="w-40 m-5" alt="doc">
            </div>
            <div class="flex justify-center ">
                <h2 class="text-xl font-bold m-3">Asistencia Médica Virtual Inmediata</h2>
            </div>
            <div class="flex justify-center m-3">
                <Form :datosRecibidos="datosDesdePadre"/>
            </div>
         
        </div>
    </div>
</template>

<script>
console.log(datosDesdePadre);

import NumericInput from './Form.vue';
export default {
    components: {
        NumericInput
    },
    name: 'Modal'
}
</script>
<style>
@import url("/assets/styles.css");
</style>