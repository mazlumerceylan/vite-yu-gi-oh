<template>
  <div id="app">
    <Header />
    <ArchetypeFilter :archetypes="archetypes" />
    <CardList />
  </div>
</template>

<script>
import CardList from './components/CardList.vue';
import ArchetypeFilter from './components/ArchetypeFilter.vue';
import Header from './components/Header.vue';

export default {
  components: {
    Header,
    ArchetypeFilter,
    CardList
  }
};
</script>

<style lang="sass">
@import './src/scss/General.scss'
@import './src/scss/Header.scss'
@import './src/scss/OptionsSection.scss'
@import './src/scss/CardList.scss'
@import './src/scss/SearchBar.scss'

</style>
