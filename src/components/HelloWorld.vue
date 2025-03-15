<script setup>
import { ref } from 'vue'

const count = ref(0);
const inputText = ref('');
const isAwesome = ref(true);
const isClicked = ref(false);

function increment() {
  count.value++;
}
function changeColor() {
  isClicked.value = !isClicked.value;
}
function toggleAwesome() {
  isAwesome.value = !isAwesome.value;
}

</script>


<template>
  <h1>Count {{ count }}</h1>

  <button @click="increment">Tambah Count</button>

  <input v-model="inputText" placeholder="Type Something">
  <p>You Typed: {{ inputText }}</p>

  <h1 :class="isClicked ? 'tittleClicked' : 'tittle'">Make me red or blue</h1>
  <button @click="changeColor">Change Color</button>

  <button @click="toggleAwesome">Toggle</button>
  <h1 v-if="isAwesome">Vue is awesome</h1>
  <h1 v-else>oh no</h1>


</template>

<style>
.tittle {
  color: red;
}
.tittleClicked {
  color: blue;
}


</style>