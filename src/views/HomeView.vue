<template>
  <router-link 
    v-for="country in sortedCountries" :key="country.cca3" :to="{ name: 'about', params: { id: country.cca3 }}">
    <div>
      <span class="pr-1">{{ country.flag }}</span>
      <span>{{ country.name.common }}</span>
    </div>
  </router-link>
</template>

<style scoped>
  .pr-1 {
    padding-right: 10px;
  }
</style>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      countries: []
    }
  },
  computed: {
    sortedCountries() {
      return this.countries.sort((a, b) => {
        if (a.name.common < b.name.common) {
          return -1;
        }
        if (a.name.common > b.name.common) {
          return 1;
        }
        return 0;
      });
    },
  },
  mounted() {
    axios.get('https://restcountries.com/v3.1/all')
      .then(response => {
        this.countries = response.data;
        console.log(this.countries[0]);
      })
      .catch(error => {
        console.log(error);
      })
  }
}
</script>
