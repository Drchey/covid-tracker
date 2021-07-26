<template>
    

    <div class="text-center">
        <h3 class="text-bold text-2xl ">{{text}}</h3>
        <div class="text-2xl mt-4 mb-7">
            {{timestamp}} 
        </div>

    </div>
  
</template>

<script>

import moment from 'moment' 

export default {
  name: 'Datatitle',
  props:['text', 'dataDate'],
  computed:{
      timestamp: function (){
          return moment(this.dataDate).format(
              'MMMM Do YYYY, h:mm:ss a'
          )

      }
  }
  
}

</script>
