<template>
  <div class="search">
    <input type="text" v-model="searchText" placeholder="Nome o Archetipo" />
    <button @click="search">Cerca</button>
    <button @click="reset">Reset</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchText: ''
    };
  },
  methods: {
    search() {
      this.$emit('search', this.searchText.trim());
    },
    reset() {
      this.$emit('reset');
    }
  }
};
</script>

<style lang="sass" scoped>

</style>
