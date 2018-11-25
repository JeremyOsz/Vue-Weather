<template id="Today">
  <p>{{weather}}</p>
</template>

<script type="text/javascript">
  module.exports = {
    data: function(){
      return{
        weather: '24 degrees'
      }
    }
  }
</script>

<style scoped>
  p {
    font-size: 2em;
    color: #999999;
  }
</style>
