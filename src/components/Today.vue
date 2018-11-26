<template id="Today">
  <p>{{weather}}</p>
</template>

<script type="text/javascript">
  const regeneratorRuntime = require("regenerator-runtime");
  module.exports = {
      data: function(){
        return{
          weather: 'Loading Weather...'
        }
      },
      methods: {
        getWeather : async () => {
          const query = 'Melbourne, AUS';
          const key = 'e3464bdda61a4808508e779d09ba81dd';
          const units = '&units=' + 'metric'
          const URL = 'https://api.openweathermap.org/data/2.5/weather?q=' + query + units + '&APPID=' + key;   
          const weather = await fetch(URL)
            .then(data=>data.json())
            .then(data=> data)
          return weather;
        },
        setWeather : (component, temp)=>{
          component.weather = temp;
        } 
      },
      created: function(){
        this.getWeather()
          .then((data)=>this.setWeather(this, data.main.temp));
      }
  }
</script>

<style scoped>
  p {
    font-size: 2em;
    color: #999999;
  }
</style>
