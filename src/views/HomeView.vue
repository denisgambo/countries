<template>
  <div class="container">
    <div v-for="country in countries" class="card" style="width: 18rem;">
      <img :src="country.flags.png" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{ country.name.common }}</h5>
        <p class="card-text"> Capitale: {{ country.capital }} <br> Population: {{ country.population }}</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: 'HomeView',
  data() {
    return {
      countries: null
    }
  },
  mounted() {
    axios.get('https://restcountries.com/v3.1/all')
      .then((response) => {
        this.countries = response.data;
        console.log(response)
      })
  }
}
</script>
