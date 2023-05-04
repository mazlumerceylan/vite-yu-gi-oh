<template>
  <div>
    <search-bar @search="search" @reset="reset"></search-bar>
    <div class="card-list">
      <p class="total-cards">Totale Carte: {{ totalResults }}</p>
      <div class="card-grid">
        <div v-if="isLoading" class="loading-spinner">
          <div class="lds-spinner">
            <div v-for="n in 12" :key="n"></div>
          </div>
        </div>
        <div class="card" v-for="card in filteredCards" :key="card.id" v-else>
          <img :src="card.card_images[0].image_url" alt="Immagine Carta" />
          <p>{{ card.name }}</p>
          <p v-if="card.archetype">Archetipo: {{ card.archetype }}</p>
          <p v-else>Archetipo: N/D</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './SearchBar.vue';
export default {
  components: {
    SearchBar
  },
  data() {
    return {
      cards: [],
      filteredCards: [],
      totalResults: 0,
      isLoading: true,
    };
  },
  async created() {
    try {
      const response = await axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php');
      this.cards = response.data.data;
      this.totalResults = this.cards.length;
      this.filteredCards = this.cards;
      this.isLoading = false;
    } catch (error) {
      console.error('Errore nel recupero dei dati:', error);
      this.isLoading = false;
    }
  },
  methods: {
    search(searchText) {
      if (searchText) {
        this.filteredCards = this.cards.filter(card => {
          const searchLowerCase = searchText.toLowerCase();
          const nameLowerCase = card.name.toLowerCase();
          const archetypeLowerCase = card.archetype ? card.archetype.toLowerCase() : '';
          return nameLowerCase.includes(searchLowerCase) || archetypeLowerCase.includes(searchLowerCase);
        });
        this.totalResults = this.filteredCards.length;
      } else {
        this.filteredCards = this.cards;
        this.totalResults = this.cards.length;
      }
    },
    reset() {
      this.filteredCards = this.cards;
      this.totalResults = this.cards.length;
    }
  }
};
</script>

<style lang="sass">
</style>