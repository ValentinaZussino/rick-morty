<template>
  <AppHeader/>
  <main>
    <AppSearch/>
    <CharactersList/>
  </main>
</template>

<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import CharactersList from './components/CharactersList.vue';
export default {
    components: { AppHeader, AppSearch, CharactersList }
}
</script>

<style lang="scss" scoped>


</style>