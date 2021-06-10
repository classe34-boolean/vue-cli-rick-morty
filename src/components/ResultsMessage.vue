<template>
  <h2 class="bg-primary p-3 text-center text-light">Trovati {{ number }} personaggi</h2>
</template>

<script>
export default {
    name: "ResultsMessage",
    props: [ "number" ]
}
</script>

<style>

</style>