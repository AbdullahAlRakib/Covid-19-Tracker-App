<template>
<main class="container" v-if="!loading">
    <div class="row">
      <div class="col-md-12">
        <div class="data-show-section text-center py-5">
          <h5><DataTitle :text="title" :dataDate="dataDate"/></h5>
        </div>
    </div>
    </div>
    <div class="row mx-5 px-5">
      <div class="col-md-12 justify-content-center ">
        <div class="databoxses-section">
          <DataBoxes :stats="stats"/>
        </div>
      </div>
      </div>
       <div class="row mx-5 px-5">
      <div class="col-md-12 justify-content-center ">
        <div class="selector-section">
          <CountrySelect @get-country="getCountryData" :countries="countries"/>
        </div>
      </div>
      </div>
</main>
<main class="container" v-else>
  <div class="row">
    <div class="col-md-12 justify-content-center mx-auto text-center py-5">
      <div class="fetch-data-show-section">
          <h5>Fetching Data....</h5>
        </div>
          <img :src="loadingImage"/>
    </div> 
  </div>

</main>
</template>

<script>
// @ is an alias to /src
import DataTitle from '@/components/DataTitle.vue'
import DataBoxes from '@/components/DataBoxes.vue'
import CountrySelect from '@/components/CountrySelect.vue'


export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect
  },
  data(){
    return{
      loading:true,
      title:'Global',
      dataDate:'',
      stats:{},
      countries:[],
      loadingImage:require('../assets/hourglass.gif')
    }
  },
  methods:{
    async fetchCovidData(){
      const res=await fetch('https://api.covid19api.com/summary')
      const data=await res.json()
      return data
    },
    getCountryData(country){
      this.stats=country
      this.title=country.Country

    }
  },
  async created(){
    const data =await this.fetchCovidData()
    
    this.dataDate=data.Date
    this.stats=data.Global
    this.countries=data.Countries
    this.loading=false

  }
}
</script>
