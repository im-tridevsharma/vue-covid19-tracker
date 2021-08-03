<template>
  <Header/>
  <main class="container" v-if="!loading">
    <Title :title="title" :datetime="dataDateTime"/>
    <DataBoxes :stats="stats"/>
    <CountrySelect @get-country="getCountryData" :countries="countries"/>
    <div class="mt-10 px-2" v-if="stats.Country">
      <button @click="clearCountryData" class="p-4 bg-green-light hover:bg-green-lighter rounded">Clear Country</button>
    </div>
  </main>
  <main class="flex flex-col items-center mt-10" v-else>
    <h3 class="text-2xl font-sans">Fetching Data</h3>
    <img :src="loadingImage" alt="loading" class="mt-10 rounded-full" width="50" height="50">
  </main>
</template>

<script>
import Header from '@/components/Header'
import Title from '@/components/Title'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: "App",
  components:{
    Header,
    Title,
    DataBoxes,
    CountrySelect
  },
  data(){
    return{
      loading: false,
      stats: '',
      title: 'Global',
      dataDateTime: '',
      countries: '',
      loadingImage: require("./assets/loader.gif")
    }
  },
  methods:{
    async fetchCovidData(){
      this.loading = true;
      const data = await fetch("https://api.covid19api.com/summary")
      return data.json()
    },
    getCountryData(country){
      this.title = country.Country,
      this.stats = country
    },
    async clearCountryData(){
      const covidData = await this.fetchCovidData()
      this.title = "Global"
      this.dataDateTime = covidData.Date;
      this.stats = covidData.Global;  
      this.countries = covidData.Countries
      this.loading = false;
    }
  },
  async created(){
    const covidData = await this.fetchCovidData()
    this.dataDateTime = covidData.Date;
    this.stats = covidData.Global;  
    this.countries = covidData.Countries
    this.loading = false;
  }
}
</script>
