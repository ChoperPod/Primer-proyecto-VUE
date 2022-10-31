<script setup>
import { ref, computed } from 'vue'
const name = 'Vue Dinámico';
const styleColor = 'color: green';
const styleColor2 = 'color: yellow';
const arrayColores = ['blue', 'red', 'blueviolet'];
const activo = true;
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
const arrayFrutasN = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    stock: 10,
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    stock: 2,
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    stock: 5,
  },
  {
    name: "Mango",
    price: "$2.00",
    description: "Un mango",
    stock: 4,
  },
  {
    name: "Naranja",
    price: "$1.50",
    description: "Una pera",
    stock: 6,
  },
];
const objetoFruta = {
  name: "Manzana",
  price: "$1.00",
  description: "Una manzana",
  Id: 1,
};

//método - methods
const handleClick = (mensaje) => {
  console.log(mensaje)
}

// codigo para ejemplo de reactividad
const counter = ref(0);
const arrayNumFav = ref([]);

const increment = () => {
  counter.value++;
}
const decrement = () => {
  counter.value--;
}
const reset = () => {
  counter.value = 0;
}
const add = () => {
  arrayNumFav.value.push(counter.value);
}

const bloquearBtnAdd = computed(() => {
  const numSearch = arrayNumFav.value.find((num) => num === counter.value);
  if (numSearch === 0) return true;
  return numSearch ? true : false;
});

const classCounter = computed(() => {
  if (counter.value === 0) {
    return "zero";
  }
  if (counter.value > 0) {
    return "positive";
  }
  if (counter.value < 0) {
    return "negative";
  }
})
</script>

<!--<template>
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
  <p v-else="!activo">Estoy Inactivo</p>
  <br>
  <h2>{{ arrayFrutas }}</h2>
  <br>
  <ul>
    <li v-for="(fruta, index) in arrayFrutas" :key="index"> {{ index }}-{{ fruta }}</li>
  </ul><br>
  <ul>
    <li v-for="(fruta, name) in arrayFrutasN" :key="fruta.name"> {{ fruta.name }} - {{ fruta.price }}
      - {{ fruta.description }}</li>
  </ul><br>
  <ul>
    <li v-for="(value, propiedad, index) in objetoFruta" :key="index">{{ index }} - {{ propiedad }} : {{ value }}</li>
  </ul>

 </template>-->

 <!--Ejemplo de V-for + V-if + Template-->
<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <br>
    <!--<ul>
    <template v-for="item in arrayFrutasN" :key="item.name">
      <li v-if="item.stock > 0">{{ item.name }} - {{ item.price }} - {{ item.stock }} - {{ item.description }}</li>
    </template>
  </ul>
  <br>
  <button v-on:click="handleClick('v-on completo')">Activame</button>
  <br><br><br>
  <button @click="handleClick('v-on abreviado')">Click Aca</button>
  <br><br>
  <button @click.left="handleClick('Click Izquierdo')">Click Izquierdo</button>
  <button @click.middle="handleClick('Click Medio')">Click Medio</button>
  <button @mouseDown.middle="handleClick('Click Medio')">Click Medio</button>
  <button @click.right.prevent="handleClick('Click Derecho')">Click Derecho</button>-->
    <h2 :class="classCounter">{{ counter }}</h2>
    <br>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="decrement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group mt-4">
      <li v-for="(num, index) in arrayNumFav" :key="index" class="list-group-item">{{ num }}</li>
    </ul>
  </div>
</template>

<style>
h1 {
  color: purple;
}

.negative {
  color: red;
}

.positive {
  color: greenyellow;
}

.zero {
  color: peru;
}
</style>