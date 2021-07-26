<template>

  <!-- View Info on Home Container -->
  <main v-if="!loading" class="flex flex-col align-center justify-center text-center">

      <Datatitle :text="title" :dataDate="dataDate" />


      <Country @get-country="getCountryData" :countries="countries"/>

      <DataBoxes :stats="stats" />

      <button
      @click="clearData()"
       v-if="stats.Country" 
       class=" bg-green-600 text-white rounded font-bold p-3 mt-10 mb-10 focus:outline-none hover:bg-green-700">
      Clear Country
      </button>
      
      
  </main>

  <main v-else class="flex flex-col align-center justify-center text-center">
      <div class="text-gray-400 text-4xl mt-5 mb-5">
        Fetching Data
      </div>
      <img :src="loadingImage" class="w-25 m-auto" alt="">
      
  </main>
</template>

<script>

import Datatitle from '@/components/Datatitle'
import DataBoxes from '@/components/DataBoxes'
import Country   from '@/components/Country'


export default {
  name: 'Home',

  components: {
    Datatitle,
    DataBoxes,
    Country,
    
   },

  // Default Data Result

  data(){
    return {
      loading:true,
      title:'Global',
      dataDate: '',
      status:{},
      countries:[],
      loadingImage : require('../assets/Spf.gif')
    }
  },
  
  // Method to Fetch Covid Data
  methods:{
    async fetchCovidInfo (){
      const res = await fetch('https://api.covid19api.com/summary') 
      const data = await res.json()
      return data
    },

    getCountryData(country){
       this.stats =country
       this.title =country.Country 

    },

    async clearData(){
        this.loading= true
        const data = await this.fetchCovidInfo()
        this.title= 'Global'
        this.stats = data.Global
        this.loading = false
        return data


    }
  },  
    async created(){
      const data = await this.fetchCovidInfo()

      this.dataDate = data.Date
      this.stats = data.Global
      this.countries = data.Countries
      this.loading = false

    }
  
}
</script>
