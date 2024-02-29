<template>
  <div>
    <div class="grid grid-cols-4 gap-5">
      <div v-for="p in products">
        <!-- <NuxtLink :to="`/products/${p.id}`">{{ p.title }}</NuxtLink> -->
        <ProductCard :product="p" />
      </div>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  layout: "products",
});

//To show Individual "title" and "description" for this page
useHead({
  title: "Nuxt App | Product",
  meta: [{ name: "description", content: "Cart Products" }],
});
//destructure "data" from api but call it as "products"
const { data: products } = await useFetch("https://fakestoreapi.com/products");
</script>

<style scoped></style>
