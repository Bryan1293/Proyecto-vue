<template>
<div>
    <h2>Formulario de registro</h2>
    <Form :validation-schema="schema" @submit="onSubmit">
        <div class="from">
        <label for="nombre">Nombre</label>
    <Field v-model="nombre" type="text" name="nombre" id="nombre"placeholder="ingrese su nombre" />
    <ErrorMessage name="nombre"></ErrorMessage>
        </div>
        <div class="from">
    <label for="nombre">Correo</label>
    <Field v-model="email" type="email" name="email" id="correo" placeholder="ingrese su email"/>
    <ErrorMessage name="email"></ErrorMessage>
        </div>
   <div class="from">
    <button type="submit">Registrar</button>
   </div>
</Form>
</div> 
</template>

<script setup>
import {Form, Field, ErrorMessage} from 'vee-validate';
import { schema } from '../schemas/validationSchema';
import {useRegistrarStore} from "../stores/registrarStore";
import { ref } from 'vue';

const registarStore = useRegistrarStore();

const nombre = ref('');
const email = ref('');

const onSubmit = () =>{
    registarStore.guardarRegistro(nombre.value, email.value);
    console.log('Se ha enviado el formulario');
}
</script>

<style>
.from {
    margin-bottom: 10px;
}
</style>