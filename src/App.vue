<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <header>
      <h2>Welcome to our Weather Station Website</h2>
    </header>
    <p>You can check the statistics of your area.</p>
    <table align = "center">
      <tr>
        <th>Time</th>
        <th><a href="#tem">Temperatur</a></th>
        <th><a href="#co">Carbon Monoxide</a></th>
        <th><a href="#gas">Gas Smoke</a></th>
        <th><a href="#air">Air Pressure</a></th>
        <th><a href="#sun">Sun Light</a></th>
      </tr>
      <tr>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
      </tr>
    </table>
    
    <div>
        <h4 id ="tem">Temperatur</h4>
          <p>We used a Temperatur Sensor to measure it.<br>
           The Esp is able to measure it with a build-in Sensor, but you can distort it easilly. 
        <h4 id = "co">Carbon Monoxide</h4>
        <h4 id = "gas">Gas Smoke</h4>
        <h4 id = "air">Air Pressure</h4>
        <h4 id = "sun">Sun Light</h4>
    </div>
  </div> 
 
  
</template>

<script>
/*import HelloWorld from './components/HelloWorld.vue'
export default {
  name: 'app',
  components: {
    HelloWorld
  }
}*/

  function temperatur(){

  }
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;
}

h2 {
  color: black;
  border: 2px, solid, rgba(104, 152, 243, 0.726);
  border-radius: 4px;
  background-color: rgba(104, 152, 243, 0.726);
}

a {
    color :#2c3e50;
    text-decoration: none;
}

table {
  color: #2c3e50;
  border: 2px, solid, rgba(255, 251, 44, 0.692);
  border-radius: 4px;
  background-color: rgba(255, 251, 44, 0.692);
}
tr, td{
  border: 1px solid #2c3e50;
  border-collapse: collapse;
  }

</style>
