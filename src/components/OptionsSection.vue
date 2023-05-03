<template>
    <div class="options-container">
      <select v-model="selectedOption" @change="onOptionChange">
        <option v-for="option in options" :key="option.id" :value="option.id">
          {{ option.text }}
        </option>
      </select>
    </div> 
</template>

<script>
export default {
  data() {
    return {
      selectedOption: null,
      options: [
        { id: 1, text: 'Option 1' },
        { id: 2, text: 'Option 2' },
        { id: 3, text: 'Option 3' },
      ],
    };
  },
  methods: {
    onOptionChange() {
      console.log('Selected option:', this.selectedOption);
    },
  },
};
</script>

<style lang="scss">

</style>
