<template>
  <div class="character text-center pb-4">
    <img class="img-fluid" :src="item.image" :alt="item.name">
    <h3>{{ item.name }}</h3>
    <div class="fst-italic">{{ item.origin.name }}</div>
    <div class="fw-bold">{{ item.species }}</div>
  </div>
</template>

<script>
export default {
    name: "Character",
    props: [ "item" ]
}
</script>

<style lang="scss">
    @import '../style/variables';

    .character {
        img {
            border-radius: 50%;
            margin-bottom: 10px;
            box-shadow: 0 0 15px 10px rgba($text-color, 0.15);
        }
    }
</style>