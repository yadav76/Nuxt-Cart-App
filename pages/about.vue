<template>
  <div>
    <h1>About</h1>
    <p>{{ data }}</p>
  </div>
</template>

<script setup>
//call "server" api
const { data } = await useFetch("/api/dummy?name=mario");
</script>

<style scoped></style>
