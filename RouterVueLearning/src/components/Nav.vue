<script>
import { RouterLink } from "vue-router";
</script>
<template>
  <div>
    <RouterLink to="/" active-class="active">Home</RouterLink>
    <RouterLink to="/about" active-class="active">About</RouterLink>
  </div>
</template>

<style scoped>
.active {
  font-weight: 900;
  color: orange;
}
</style>
