<template>
    <div class="q-pa-md row items-start q-gutter-md">
       <q-card >
      <q-card-section>
          <q-list >
                <q-item >
        <q-item-section><q-btn color="primary" label="Buy" class="btn-fixed-width text-overline" /></q-item-section>
        <q-item-section side><q-btn color="white" text-color="black" label="Sell" class="btn-fixed-width text-overline" /></q-item-section>
      </q-item>
             <q-item >
               <q-item-section> <q-btn-dropdown class="text-overline" color="primary" label="Order Type"> 
      <q-list>
        <q-item clickable v-close-popup @click="onItemClick">
          <q-item-section>
            <q-item-label>Limited Order</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-btn-dropdown>
    </q-item-section>
           </q-item>
        <q-item  >
        <q-item-section>
            <q-input class="text-overline" outlined v-model="text" label="Order Size" >
        <template v-slot:append>
          <q-icon name="attach_money" />
        </template>
      </q-input>
        </q-item-section>
      </q-item>
       <q-item  >
        <q-item-section>
              <q-input height=1em outlined v-model="text" label="Price" class="text-overline" >
        <template v-slot:append>
          <q-icon name="attach_money" />
        </template>
      </q-input>
        </q-item-section>
      </q-item>
       <q-item  >
        <q-item-section>
            <q-btn color="primary" label="Buy Order" class="text-overline" />
        </q-item-section>
      </q-item>
      <q-item  >
          <q-item-section text-color="primary">
              <div class="text-center" text-color="white">
              <span class="text-right text-overline" >Create</span><span class="text-primary text-overline"> Auto Sale?</span>
              </div>
          </q-item-section>
      </q-item>
          </q-list>
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
.btn-fixed-width
  width 100px
</style>
