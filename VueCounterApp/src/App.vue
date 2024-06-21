<script setup>
import {ref} from "vue"
  const count = ref(0);
</script>

<template>
    <main>
      <div>
        <h4>The curren count is...</h4>
      </div>
      <h1>{{count}}</h1>
      <div style="display: flex;">
        <button @click="count--">-</button>
        <button @click="count++">+</button>
      </div>
    </main>
</template>

<style scoped>
  main{
    color: black;
    background-color: aliceblue;
    height: 100vh;
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
</style>
