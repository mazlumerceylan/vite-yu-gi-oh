<template>
  <div class="card-list">
    <div class="title">
    <h1>Yu-Gi-Oh!</h1>
    </div>
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
      this.totalResults = response.data.total_results;
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  }
};
</script>

<style scoped>
.card-list {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
  font-family: 'Arial', sans-serif;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
}

.card {
  background-color: #f9f9f9;
  border-radius: 8px;
  padding: 1rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.card img {
  max-width: 100%;
  height: auto;
  border-radius: 4px;
}

.card p {
  margin-top: 0.5rem;
}
</style>
