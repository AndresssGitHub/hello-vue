<script setup>
import { ref, computed } from "vue";

const name = "Vue 3";

const counter = ref(0);

const arrayCounter = ref([]);

const increment = () => { counter.value++; };

const decrement = () => { counter.value--; };

const reset = () => { counter.value = 0; };

const add = () => {
  arrayCounter.value.push(counter.value)
};
 
const blockNumber = computed(() => {
  const number = arrayCounter.value.find((num => 
  num === counter.value));
  if(number === 0) return true;
  return number ? true : false;
});


const classCounter = computed(() => {
  if(counter.value === 0){
    return 'zero'
  }
  if(counter.value > 0){
    return 'positive'
  }
  if(counter.value < 0){
    return 'negative'
  }
})
</script>

<template>
  <div class="container">
    <h1>Hello {{ name }}!</h1>
    <h2 :class="classCounter"> {{ counter }} </h2>
    <button  @click="increment" >Incremet</button>
    <button  @click="decrement">Decrement</button>
    <button  @click="reset">Reset</button>
    <button  @click="add" :disabled="blockNumber">Add</button>
    <br>
    {{ arrayCounter }}
    <ul>
      <li v-for="(item, index) in arrayCounter" :key="index">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<style>
.negative {
    color: red;
}

.positive {
    color: green;
}

.zero {
  color:blue
}
</style>