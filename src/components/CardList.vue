<template>
  <div class="card-list">
    <p class="total-cards">Total Cards: {{ totalResults }}</p>
    <div class="card-grid">
      <div v-if="isLoading" class="loading-spinner">
        <div class="lds-spinner">
          <div v-for="n in 12" :key="n"></div>
        </div>
      </div>
      <div class="card" v-for="card in cards" :key="card.id" v-else>
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
      totalResults: 0,
      isLoading: true
    };
  },
  async created() {
    try {
      const response = await axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php');
      this.cards = response.data.data;
      this.totalResults = this.cards.length;
      this.isLoading = false;
    } catch (error) {
      console.error('Error fetching data:', error);
      this.isLoading = false;
    }
  }
};
</script>


<style lang="sass">

</style>
