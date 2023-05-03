<template>
  <div id="app">
    <Header />
    <CardList />
  </div>
</template>

<script>
import CardList from './components/CardList.vue';
import Header from './components/Header.vue';

export default {
  components: {
    Header,
    CardList
  }
};
</script>

<style lang="sass">
 @import './assets/scss/CardList.scss'
 @import './assets/scss/General.scss'
 @import './assets/scss/Header.scss'

</style>
