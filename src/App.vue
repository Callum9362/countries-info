<template>
  <div>
    <ul>
      <li v-for="country in countries" :key="country.alpha3Code">{{ country.name.common }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      countries: []
    }
  },
  mounted() {
    axios.get('https://restcountries.com/v3.1/all')
      .then(response => {
        this.countries = response.data;
        console.log(this.countries);
      })
      .catch(error => {
        console.log(error);
      })
  }
}
</script>
