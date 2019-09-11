<template>
  <header class="flex">
    <h1 class="text-3xl">Dad Jokes</h1>
    <ul class="flex">
      <li>
        <nuxt-link to="/">Home</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/jokes">Jokes</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/about">About</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "AppHead"
};
</script>

<style scoped>
</style>