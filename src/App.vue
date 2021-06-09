<template>
  <div id="app">
    <Header msg="Rick & Morty app" />

    <main>
      <CharactersList />
    </main>
  </div>
</template>

<script>
import Header from './components/Header';
import CharactersList from './components/CharactersList';

export default {
  name: 'App',
  components: {
    Header,
    CharactersList
  }
}
</script>

<style lang="scss">
  @import './style/general';
</style>
