<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  methods: {
    addToCount() {
      this.count++
    },

    subtractFromCount() {
      this.count--
    }
  },
}
</script>

<template>
  <main>
    <div>
      <h4>The curren count is...</h4>
      <h1>
        {{count}}
      </h1>
      <button @click="subtractFromCount()">-</button>
      <button @click="addToCount()">+</button>
    </div>
  </main>
</template>

<style scoped>
  main{
    background-color: aliceblue;
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  div{
    text-align: center;
  }
</style>
