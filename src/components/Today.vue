<template id="Today">
  <p>{{weather}} degrees</p>
</template>

<script type="text/javascript">
const regeneratorRuntime = require("regenerator-runtime");
module.exports = {
  props: {
    query: {
      type: String,
      required: true
    }
  },
  data: function() {
    return {
      weather: "Loading Weather..."
    };
  },
  methods: {
    getWeather: async function() {
      const query = this.query;
      const key = "e3464bdda61a4808508e779d09ba81dd";
      const units = "&units=" + "metric";
      const URL =
        "https://api.openweathermap.org/data/2.5/weather?q=" +
        query +
        units +
        "&APPID=" +
        key;
      const weather = fetch(URL)
        .then(data => data.json())
        .then(data => data);
      return await weather;
    },
    setWeather: (component, temp) => {
      component.weather = temp;
    }
  },
  created: function() {
    this.getWeather()
      .then(data => this.setWeather(this, data.main.temp))
      .catch(error => {
        this.setWeather(this, "Problem fetching weather data - Invalid Query");
        console.error(
          new Error("Problem fetching weather data - Invalid Query")
        );
      });
  },
  watch: {
    query: function(newVal, oldVal) {
      console.log("query changed to: " + newVal);
      this.getWeather()
        .then(data => this.setWeather(this, data.main.temp))
        .catch(error => {
          this.setWeather(
            this,
            "Problem fetching weather data - Invalid Query"
          );
          console.error(
            new Error("Problem fetching weather data - Invalid Query")
          );
        });
    }
  }
};
</script>

<style scoped>
p {
  font-size: 2em;
  color: #999999;
}
</style>
