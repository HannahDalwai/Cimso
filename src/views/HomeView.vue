<template>
<div v-if="payload">
  <div v-for="data in payload" :key="data">
    <div v-for="payload in data" :key="payload">
      <h2>
        {{payload}}
      </h2>
    </div>
 </div>
</div>
 <div v-else>
  <h1>
    Loading...
  </h1>
 </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
export default {
  components: {
 
  },
  data(){
    return{
     payload:null
    }
  },
  mounted(){ 
 
    axios.get('https://apitest.cimsoweb.com/api/innterchange/get_booking_units_request')
    .then(res => {
      this.payload = res.data
      console.log(this.payload)
    })
    .catch(err => {
      console.error(err); 
    })

}}
</script>