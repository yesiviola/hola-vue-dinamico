<template>
  <div class="container text-center">
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <h2 :class="classCounter">{{ counter }}</h2>
  <button @click="increment" class="btn btn-success">increment</button>
  <button @click="decrement" class="btn btn-danger">Decrement</button>
  <button @click="reset" class="btn btn-secondary">Reset</button>
  <button @click="add" class="btn btn-primary">Add</button>
  </div>
  <ul class="list-group">
    <li
    class="list-group-item"
     v-for="(num,index) in arrayfavoritos"
      :key="index">
        {{ num }}

    </li>
  </ul>
</template>

<script setup>
import {ref, computed}from 'vue'
const name = "vue dinamico";
const counter = ref (0);
const arrayfavoritos = ref ([]);

const increment = () => {
  counter.value++;
};

const decrement = () => {
  counter.value --;
};

const reset = () => {
  counter.value = 0;
};
const add = ()=> {
  arrayfavoritos.value.push(counter.value);
};

const classCounter = computed(()=> {
  if (counter.value === 0) {
return "zero"
}else if (counter.value > 0) {
return "positive";
} else{
return "negative";
}
});
</script>

<style>
h1 {
  color:red;
}
.positive{
  color:green;
}
.negative{
  color:red;
}
</style>
