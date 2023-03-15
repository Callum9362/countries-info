<template>
  <div>
    <h1>{{ country.name.common }}</h1>
    <p>Capital: {{ country.capital }}</p>
    <p>Population: {{ country.population }}</p>
    <p>Region: {{ country.region }}</p>
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
  async created() {
    const response = await axios.get(`https://restcountries.com/v3.1/alpha/${this.$route.params.id}`);
    this.country = response.data[0];
  },
}
</script>