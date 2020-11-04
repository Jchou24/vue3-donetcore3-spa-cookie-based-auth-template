<template>
  <div class="">
    {{weather}}
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
import axios from 'axios';

export default defineComponent({
  name: 'TestWeatherAPI',
  setup(){
    const weather: any = ref([123]);

    onMounted(()=>{
      axios.get(process.env.VUE_APP_SERVER_URL + 'WeatherForecast').then(response =>{
        weather.value = response.data
        console.log(weather)
      });
    })

    return {
      weather
    }
  }

});
</script>

