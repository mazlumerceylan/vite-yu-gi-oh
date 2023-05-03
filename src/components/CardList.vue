<template>
  <div class="card-list">
    <p class="total-cards">Total Cards: {{ totalResults }}</p>
    <div class="card-grid">
      <div class="card" v-for="card in cards" :key="card.id">
        <img :src="card.card_images[0].image_url" alt="Card image" />
        <p>{{ card.name }}</p>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios';

export default {
  data() {
    return {
      cards: [],
      totalResults: 0
    };
  },
  async created() {
    try {
      const response = await axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php');
      this.cards = response.data.data;
      this.totalResults = this.cards.length; // Calcola il totale delle carte utilizzando la lunghezza dell'array
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  }
};
</script>


<style lang="sass">


</style>
