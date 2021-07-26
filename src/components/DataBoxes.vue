<template>
  <div class="grid md:grid-cols-2 gap-3">

    <!--Cases -->
    <div class="shadow-md bg-red-200 p-5 text-center">
      <h3 class="text-3xl text-red-600 font-bold mb-4">
        Cases
      </h3>

      <div class="text-2xl mb-4">
          <span class="font-bold text-gray-700">New:</span>
          {{stats.NewConfirmed}}
      </div>

       <div class="text-2xl mb-4">
          <span class="font-bold text-gray-700">Total:</span>
          {{stats.TotalConfirmed}}
      </div>

       <div class="text-2xl mb-4">
          <span class="font-bold text-gray-700">Recovered:</span>
          {{stats.TotalRecovered}}
      </div>

    </div>

   <!--- Total Deaths -->

    <div class="shadow-md bg-red-400 p-5 text-center">
      <h3 class="text-3xl text-red-600 font-bold mb-4">
        Deaths
      </h3>

      <div class="text-2xl mb-4">
          <span class="font-bold text-gray-700">New:</span>
          {{stats.NewDeaths}}
      </div>

       <div class="text-2xl mb-4">
          <span class="font-bold text-gray-700">Total:</span>
          {{stats.TotalDeaths}}
      </div>

       <div class="text-2xl mb-4">
          <span class="font-bold text-gray-700">Recovered:</span>
          {{stats.TotalRecovered}}
      </div>

    </div>
  </div>
</template>


<script>


export default {
  name: 'DataBoxes',
  props: ['stats'],
}
</script>
