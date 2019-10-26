<template>
  <div id="app">
    <header>
      <h2>Welcome to our Weather Station Website</h2>
    </header>
    <p>You can check the statistics of your area.</p>
    <table align="center">
      <tr>
        <th>Date and Time</th>
        <th>Longitude</th>
        <th>Latitude</th>
        <th><a href="#tem">Temperature</a></th>
        <th><a href="#co">Carbon Monoxide</a></th>
        <th><a href="#hum">Humidity</a></th>
        <th><a href="#air">Air Pressure</a></th>
        <th><a href="#bri">Brightness</a></th>
      </tr>
      <tr>
        <td>test</td>
        <td>test</td>
        <td>test</td>
        <td>test</td>
        <td>test</td>
        <td>test</td>
        <td>test</td>
        <td>test</td>
      </tr>
    </table>

    <div>
        <h4 id ="tem">Temperature</h4>
          <p>We used a "DHT11 Temperature & Humidity Sensor Module" to measure it.<br>
           The Esp32 is able to measure it with a build-in Sensor, but you can distort it easilly.
           You can also measure the air humidity. 
          </p>
        <h4 id = "co">Carbon Monoxide</h4>
          <p>For measuring the Carbon Monoxide in the air, we used the "MQ-7 CO Carbon MonoxideDetector Sensor Modeule".</p>
        <h4 id = "hum">Gas Smoke</h4>
          <p>With the "MQ-2 Gas Smoke Sensor Module"</p>
        <h4 id = "air">Air Pressure</h4>
          <p>"BMP180 Digital Barometric Pressure Sensor Module"</p>
        <h4 id = "bri">Sun Light</h4>
          <p>"Photosensitive Light Sensor Module"</p>
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
html {
  scroll-behavior: smooth;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
  margin-left:10%;
  margin-right: 10%;
  
}

header {
  color: white;
  border: 2px, solid, rgba(104, 152, 243, 0.726);
  border-radius: 4px;
  background-color: rgba(104, 152, 243, 0.726);
  border-width: 20%;
}

a {
    color :white;
    text-decoration: none;
}

th {
  color: white;
  border: 2px, solid, #2c3e50;
  border-radius: 4px;
  border-width: 20%;
  background-color: #2c3e50;
  padding:4px;
}
td{
  border: 1px solid #2c3e50;
  border-collapse: collapse;
}
h4 {
  color: white;
  border: 2px, solid, rgba(104, 152, 243, 0.726);
  border-radius: 4px;
  margin-left: 20%;
  margin-right: 20%;
  background-color: rgba(104, 152, 243, 0.726);
  border-radius: 4px;
}

p {
  border: 2px, hidden, rgba(104, 152, 243, 0.726);
  margin-left: 20%;
  margin-right: 20%;
  text-align: center;
}
</style>
