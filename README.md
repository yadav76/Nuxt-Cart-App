### Nuxt case-218

# Nuxt is a framework that has more power and muscle as compare to vue.js

### adding Tailwind to Nuxt app

visit - https://nuxt.com/modules/tailwindcss
run command - npm install --save-dev @nuxtjs/tailwindcss

add this in nuxt.config.ts -
export default defineNuxtConfig({
modules: ['@nuxtjs/tailwindcss']
})

//add all the classes names in files in which want to apply tailwind styles

### Now configure additional styles together in assets/css/tailwind.css

### Fetching Data

useFetch() function allows us to fetch data from any "API,"

### Reusable Components

make custom components which are not imported mannually. It will be imported directly by Nuxt.

### Error Pages

When user visits any unknown page then the error page should be shown
When I try to fetch any data from API which is not available then I want to show an error page so I can throw and error

if (!product.value) {
throw createError({ statusCode: 404, statusMessage: "Product Not Found!" });
}

### To show MetaData like title of page, description on every page add below lines in "nuxt.config.ts" file

app: {
head: {
title: "Nuxt Cart App",
meta: [{ name: "description", content: "Everything about Nuxt" }],
link: [
{
rel: "stylesheet",
href: "https://fonts.googleapis.com/icon?family=Material+Icons",
},
],
},
},

## To apply Individual "title" of page and "description" I can write below code in that page

useHead({
title: "Nuxt App | Product",
meta: [{ name: "description", content: "Cart Products" }],
});

## Another way to write "title" of page and "description" I can write below code in that page

I can use this built in component also

<Head>
    <Title>Nuxt App | {{ product.title }}</Title>
    <Meta name="description" :content="product.description" />
</Head>

### Server Routes

Any code or API that we don't want to expose for that we use server Routes. Like Authentication Api endpoint. For this create a "server" Global Folder and "api" folder inside 'server' folder

to visit this server api we have to call "/api/fileName"
write this type of message in custom "server" api

export default defineEventHandler(() => {
return {
message: `Hello Nuxt`,
};
});

Now call this api from "about" page
