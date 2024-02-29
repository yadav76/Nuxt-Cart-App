<template>
  <div>
    <Head>
      <Title>Nuxt App | {{ product.title }}</Title>
      <Meta name="description" :content="product.description" />
    </Head>

    <ProductDetails :product="product" />
  </div>
</template>

<script setup>
const { id } = useRoute().params;
const uri = "https://fakestoreapi.com/products/" + id;

//fetch the product
//useFetch() try to minimize our work and it fetches same data for all products. So that's why I have added
//{ key: id } inside useFetch() function.
const { data: product } = await useFetch(uri, { key: id });

//If there is no product found for any data then throw an error
if (!product.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Product Not Found!",
    fatal: true,
  });
}

definePageMeta({
  layout: "products",
});
</script>

<style scoped></style>
