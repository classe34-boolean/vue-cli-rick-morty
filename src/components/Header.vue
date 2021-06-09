<template>
  <header class="my-5">
      <h1 class="text-center">{{ msg }}</h1>
  </header>
</template>

<script>
export default {
    name: "Header",
    props: { "msg": String }
}
</script>

<style>

</style>