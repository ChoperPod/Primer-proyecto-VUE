<script setup>
const name = 'Vue Dinámico';
const styleColor = 'color: green';
const styleColor2 = 'color: yellow';
const arrayColores = ['blue', 'red', 'blueviolet'];
const activo = true;
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <br>
  <h2>{{ arrayColores }}</h2>
  <br>
  <h2 v-bind:style="styleColor">Soy verde</h2>
  <br>
  <h2 :style="styleColor2">soy V-bind abreviado</h2>
  <br>
  <h2 :style="`color: ${arrayColores[1]}`">soy color desde un array</h2>
  <br>
  <h2 :style="`color: ${arrayColores[2]}`">{{ activo ? 'Estoy Activo' : 'Estoy Inactivo' }}</h2>
  <br>
  <p v-if="activo">Estoy Activo</p>
  <p v-else = "!activo">Estoy Inactivo</p>
</template>

<style>
h1 {
  color: red;
}
</style>