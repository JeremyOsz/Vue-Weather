<template>
  <div id="app">
    <div id="app">
      <h1>Weather App</h1>
      <p>The weather today in {{query}} is:</p>
      <form @submit.prevent="setQuery()">
        <input type="text" id="city" v-model="search">
        <button type="submit">Search</button>
      </form>
      <today v-bind:query="query"></today>
    </div>
  </div>
</template>

<script>
import today from "./components/Today.vue";

export default {
  name: "app",
  data() {
    return {
      search: "",
      query: "Melbourne"
    };
  },
  components: {
    today
  },
  methods: {
    setQuery: function() {
      this.query = this.search;
    },
    getQuery: function() {
      return this.query;
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
