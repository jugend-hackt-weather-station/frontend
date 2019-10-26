<template>
<div id="app">
  <div class="topnav">
    <a href="#tem">Temperature | </a>
    <a href="#co">Carbon Monoxide | </a>
    <a href="#hum">Humidity | </a>
    <a href="#air">Air Pressure | </a>
    <a href="#bri">Brightness</a>
  </div>
    <header>
      <h2>Welcome to Open Weather Station</h2>
    </header>
    <p>Here you can check the statistics from your Open Weather Station.</p>
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
      <tr v-for="(row, idx) in data" :key="`row-${idx}`">
        <td>{{formatDateTime(row.datetime)}}</td>
        <td>{{cutDecimals(row.longitude, 2)}}</td>
        <td>{{cutDecimals(row.latitude, 2)}}</td>
        <td>{{row.temperature}}</td>
        <td>{{row.carbonmonoxide}}</td>
        <td>{{row.humidity}}</td>
        <td>{{row.pressure}}</td>
        <td>{{row.brightness}}</td>
      </tr>
    </table>

    <div class="text">
        <h4 id ="tem">Temperature</h4>
          <p>We used a "DHT11 Temperature & Humidity Sensor Module" to measure it.<br>
           The Esp32 is able to measure it with a build-in Sensor, but you can distort it easilly.
           You can also measure the air humidity. 
          </p>
        <h4 id = "co">Carbon Monoxide</h4>
          <p>For measuring the Carbon Monoxide in the air, we used the "MQ-7 CO Carbon MonoxideDetector Sensor Modeule".</p>
        <h4 id = "hum">Humidity</h4>
          <p>With the "MQ-2 Gas Smoke Sensor Module"</p>
        <h4 id = "air">Air Pressure</h4>
          <p>"BMP180 Digital Barometric Pressure Sensor Module"</p>
        <h4 id = "bri">Brightness</h4>
          <p>"Photosensitive Light Sensor Module"</p>
    </div>
    <p><br></p>
  </div> 
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
        data: []
    }
  },
  async created() {
    const res = await axios({
      method: 'get',
      url: "http://localhost:5000/getAll",
      validateStatus: () => true,
    })

    if(res.status == 200 && Array.isArray(res.data)) {
      this.data = res.data.sort((o1, o2) => o1.datetime - o2.datetime)
      console.log(this.data)
    } else {
        console.error(res.data)
    }
  },
  methods: {
      formatDateTime(datetime) {
        let date = new Date(datetime)

        return `${date.getFullYear()}/${this.padDigits(date.getMonth()+1, 2)}/${this.padDigits(date.getDate(), 2)} ${this.padDigits(date.getHours(), 2)}:${this.padDigits(date.getMinutes(), 2)}:${this.padDigits(date.getSeconds(), 2)}`
      },
      padDigits(number, digits) {
        return Array(Math.max(digits - String(number).length + 1, 0)).join(0) + number;
      },
      cutDecimals(str, digits) {
        return str.slice(0, str.indexOf(".")+digits+1)
      }
  }
}
</script>

<style lang="scss">
html {
  scroll-behavior: smooth;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 5%;
  margin-right: 5%;
  border: 2px, solid, rgba(236, 236, 235, 0.705);
  background: rgba(236, 236, 235, 0.705);
  border-radius: 4px;
}

header {
  color: white;
  border: 2px, solid, rgba(104, 152, 243, 0.726);
  border-radius: 4px;
  background-color: rgba(104, 152, 243, 0.726);
  border-width: 20%;
}

a {
  color: white;
  text-decoration: none;
}

th {
  color: white;
  border: 2px, solid, #2c3e50;
  border-radius: 4px;
  border-width: 20%;
  background-color: #2c3e50;
  padding: 4px;
}
td {
  border: 1px solid #2c3e50;
  background-color: white;
  border-collapse: collapse;
}
h4 {
  color: white;
  border: 2px, solid, rgba(104, 152, 243, 0.726);
  border-radius: 4px;
  margin-left: 20%;
  margin-right: 20%;
  background-color: rgba(104, 152, 243, 0.726);
}

.text {
  border: 2px, hidden, rgba(104, 152, 243, 0.726);
  background-color: white;
  border-radius: 4px;
  height: 10%;
  margin-left: 20%;
  margin-right: 20%;
  text-align: center;
  padding-bottom: 2px;
}

.topnav {
  border: 2px, solid, #2c3e50;
  background: #2c3e50;
  border-radius: 4px;
  background-color: #2c3e50;
  color: white;
  font-weight: bold;
  padding: 2px;
}
</style>
