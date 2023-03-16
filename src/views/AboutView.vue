<template>
  <div>
    <h1>{{ country.name.common }}</h1>
    <p>Capital: {{ country.capital[0] }}</p>
    <p>Population: {{ formattedPopulation }}</p>
    <p>Region: {{ country.region }}</p>
    <p>Timezone: {{ country.timezones[0] }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'About',
  data() {
    return {
      country: {},
    }
  },
  computed: {
    formattedPopulation() {
      if (this.country.population) {
        return this.country.population.toLocaleString();
      } else {
        return '';
      }
    }
  },
  async created() {
    const response = await axios.get(`https://restcountries.com/v3.1/alpha/${this.$route.params.id}`);
    this.country = response.data[0];
    console.log(this.country);
  },
}
</script>