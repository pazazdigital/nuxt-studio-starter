<script setup lang="ts">
const route = useRoute();

const { data: page } = await useAsyncData("page-" + route.path, () => {
  return queryCollection("content").path(route.path).first();
});

if (!page.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Page not found",
    fatal: true,
  });
}
</script>

<template>
  <ContentRenderer v-if="page" :value="page" />
</template>

<style>
body {
  @apply bg-gray-100 text-gray-800 p-4;
}
h1,
h2,
h3,
h4,
h5,
h6,
p,
ul,
ol {
  @apply mb-4;
}
h1 {
  @apply text-4xl font-bold;
}
a {
  @apply text-blue-500 underline;
}
</style>
