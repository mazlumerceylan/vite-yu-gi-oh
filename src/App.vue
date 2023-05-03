<template>
  <div id="app">
    <Header />
    <OptionsSection />
    <CardList />
  </div>
</template>

<script>
import CardList from './components/CardList.vue';
import OptionsSection from './components/OptionsSection.vue';
import Header from './components/Header.vue';

export default {
  components: {
    Header,
    OptionsSection,
    CardList
  }
};
</script>

<style lang="sass">
@import './src/scss/General.scss'
@import './src/scss/Header.scss'
@import './src/scss/OptionsSection.scss'
@import './src/scss/CardList.scss'

</style>
