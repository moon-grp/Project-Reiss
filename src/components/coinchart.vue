<template>
<q-page>
    <div>
        <VueApexCharts width=90% v-if="series" type=candlestick :options="plotOptions" :series="series"></VueApexCharts>
    </div>
</q-page>
</template>

<script>
import ApexCharts from 'apexcharts'
import VueApexCharts from 'vue-apexcharts'
import axios from 'axios'

export default {
    name:'coinchart',
     components: {
     VueApexCharts,
  },
      created(){
        axios.get('https://min-api.cryptocompare.com/data/histominute?fsym=BTC&tsym=USD&limit=10')
        .then(
            Response=>
            {
              console.log(Response.data.Data[0].time)
             //still goin to fix issues with data to candle stick
            })
            .catch(
               e =>{
                console.log(e)
            }
            )
            
            
            
            },
  data() {
    return {
     plotOptions: {
  candlestick: {
    wick: {
      useFillColor: true,
    }
  }
},
    series: [{
  data: [{
    x: 1565569500,
    y: [11505.14, 11507.99, 11505.14, 11506.47]
  },
 {
    x: 1565569560,
    y: [11506.47, 11506.47, 11486.49, 11489.2]
  }, 
   {
    x: 1565569620,
    y: [11489.2, 11497.79, 11489.1, 11494.35]
  }, 
   {
    x: 1565569680,
    y: [ 11494.35, 11496.01, 11487.49, 11496.01]
  }, 
    {
    x: 1565569740,
    y: [11496.01, 11498.41, 11494.38, 11494.38]
  }, 
 ]
}]
    }
  }


}





</script>

<style>
#chart {
  max-width: 650px;
  margin: 35px auto;
}
</style>
