<template>
    <div class="q-pa-md row items-start q-gutter-md">
       <q-card >
      <q-card-section>
          <p>Price Compare</p>
      <div class="q-pa-md" >
          <q-list separator>
                <q-item >
        <q-item-section>Bitcoin</q-item-section>
        <q-item-section side>$ {{BTC}}</q-item-section>
      </q-item>
             <q-item >
        <q-item-section>Ethereum</q-item-section>
        <q-item-section side>$ {{ETH}}</q-item-section>
      </q-item>
        <q-item  >
        <q-item-section>Litecoin</q-item-section>
        <q-item-section side>$ {{LTC}}</q-item-section>
      </q-item>
       <q-item  >
        <q-item-section>XRP</q-item-section>
        <q-item-section side>$ {{XRP}}</q-item-section>
      </q-item>
       <q-item  >
        <q-item-section>Bitcoin Gold</q-item-section>
        <q-item-section side>$ {{BTG}}</q-item-section>
      </q-item>
          </q-list>
      </div>
      </q-card-section>
    </q-card>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'pricecompare',
    data () {
    return {
       BTC:null,
       ETH: null,
       LTC:null,
       XRP: null,
       BTG: null 
    }
    },
    created(){
        axios.get('https://min-api.cryptocompare.com/data/pricemulti?fsyms=BTC,ETH,LTC,XRP,BTG&tsyms=USD')
        .then(
            Response=>
            {
               this.BTC=Response.data.BTC.USD
                this.ETH=Response.data.ETH.USD
                this.LTC=Response.data.LTC.USD
                this.XRP=Response.data.XRP.USD
                this.BTG=Response.data.BTG.USD
                

            }
        )
        .catch(
            e =>{
                console.log(e)
            }
        )

    }

}
</script>

<style lang="stylus" scoped>

</style>