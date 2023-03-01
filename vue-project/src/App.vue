<script setup>
import {ref,computed} from 'vue';
  const name = 'Vue dinámico';

  const counter = ref(0);
  const arrayNum =ref([]);

  const increment = () =>{
    counter.value++;
  }

  const decrease = () =>{
    counter.value--;
  }

  const reset = () =>{
    counter.value=0;
  }

  const classCounter = computed(()=>{
    if(counter.value === 0){
      return 'zero';
    }
    else if(counter.value >0){
      return 'positive';
    }
    else{
      return 'negative';
    }
  });

  const addNum = () =>{
    arrayNum.value.push(counter.value);
  }

  const disableButton = computed(()=>{
    return arrayNum.value.includes(counter.value);
  })
          
</script>

<template>
  <div class="container text-center mt-3">
    <h1>Projecto {{ name.toUpperCase() }}</h1>
    <h2 :class="classCounter">
          {{ counter }}
      </h2>
    <div class="btn-group" role="group" aria-label="Basic example">
      <button @click="increment()" class="btn btn-success">Incrementar</button>
      <button @click="decrease()" class="btn btn-danger">Disminuir</button>
      <button @click="reset()" class="btn btn-secondary">Resetear</button>
      <button @click="addNum()" :disabled="disableButton" class="btn btn-primary">Añadir número</button>
    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="num in arrayNum" :key="num">{{ num }}</li>
    </ul>
</div>

</template>

<style>
h1{
  color: cadetblue;
}

.negative {
    color: red;
}

.positive {
    color: green;
}

.zero{
  color: peru;
}

</style>