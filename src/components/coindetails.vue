<template>
      <div class="q-pa-md">
    <q-table
      class="text-h6"
      title="Coin Details"
      :data="data2"
      :columns="columns"
      row-key="name"
    >
     <template v-slot:body-cell-imgurl="props" >
           <q-td> 
             <q-avatar square size="40px">
              <img  :src=props.value>
              </q-avatar>
           </q-td>
        </template>
        
    </q-table>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'coindetails',
     methods: {
   
  },
    created(){
        axios.get('https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH,LTC,XRP,BCH&tsyms=USD')
        .then(
            Response=>
            {
               console.log(Response.data.DISPLAY.BTC)
               this.data2[0].price=Response.data.DISPLAY.BTC.USD.PRICE
               this.data2[0].imgurl="https://cryptocompare.com" + Response.data.DISPLAY.BTC.USD.IMAGEURL
               this.data2[0].directvol=Response.data.DISPLAY.BTC.USD.VOLUME24HOURTO
               this.data2[0].totalvol=Response.data.DISPLAY.BTC.USD.TOTALVOLUME24HTO
               this.data2[0].marketcap=Response.data.DISPLAY.BTC.USD.MKTCAP
               this.data2[1].price=Response.data.DISPLAY.ETH.USD.PRICE
               this.data2[1].imgurl="https://cryptocompare.com" + Response.data.DISPLAY.ETH.USD.IMAGEURL
               this.data2[1].directvol=Response.data.DISPLAY.ETH.USD.VOLUME24HOURTO
               this.data2[1].totalvol=Response.data.DISPLAY.ETH.USD.TOTALVOLUME24HTO
               this.data2[1].marketcap=Response.data.DISPLAY.ETH.USD.MKTCAP
               this.data2[2].price=Response.data.DISPLAY.LTC.USD.PRICE
               this.data2[2].imgurl="https://cryptocompare.com" + Response.data.DISPLAY.LTC.USD.IMAGEURL
               this.data2[2].directvol=Response.data.DISPLAY.LTC.USD.VOLUME24HOURTO
               this.data2[2].totalvol=Response.data.DISPLAY.LTC.USD.TOTALVOLUME24HTO
               this.data2[2].marketcap=Response.data.DISPLAY.LTC.USD.MKTCAP
               this.data2[3].price=Response.data.DISPLAY.XRP.USD.PRICE
               this.data2[3].imgurl="https://cryptocompare.com" + Response.data.DISPLAY.XRP.USD.IMAGEURL
               this.data2[3].directvol=Response.data.DISPLAY.XRP.USD.VOLUME24HOURTO
               this.data2[3].totalvol=Response.data.DISPLAY.XRP.USD.TOTALVOLUME24HTO
               this.data2[3].marketcap=Response.data.DISPLAY.XRP.USD.MKTCAP
               this.data2[4].price=Response.data.DISPLAY.BCH.USD.PRICE
               this.data2[4].imgurl="https://cryptocompare.com" + Response.data.DISPLAY.BCH.USD.IMAGEURL
               this.data2[4].directvol=Response.data.DISPLAY.BCH.USD.VOLUME24HOURTO
               this.data2[4].totalvol=Response.data.DISPLAY.BCH.USD.TOTALVOLUME24HTO
               this.data2[4].marketcap=Response.data.DISPLAY.BCH.USD.MKTCAP

            }
        )
        .catch(
            e =>{
                console.log(e)
            }
        )

    },
data () {
    return {
      columns: [
        { name: 'imgurl', field: 'imgurl' },
        {
          name: 'name',
          required: true,
          label: 'Coin',
          align: 'left',
          field: row => row.name,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'price', align: 'center', label: 'Price', field: 'price', sortable: true },
        { name: 'directvol', label: 'Direct Vol.24H', field: 'directvol', sortable: true },
        { name: 'totalvol', label: 'Total Vol.24H', field: 'totalvol' },
        { name: 'marketcap', label: 'Market Cap.', field: 'marketcap' },
        
      ],
      data2: [
        {
        
          name: 'Bitcoin',
          price: '',
          imgurl: '',
          directvol:'',
          totalvol:'',
          marketcap:''
        },
        {
         name: 'Ethereum',
          price: '',
          imgurl: '',
          directvol:'',
          totalvol:'',
          marketcap:''
        },
        {
            name: 'Litecoin',
          price: '',
          imgurl: '',
          directvol:'',
          totalvol:'',
          marketcap:''
        },
        {
            name: 'XRP',
          price: '',
          imgurl: '',
          directvol:'',
          totalvol:'',
          marketcap:''
        },
        {
          name: 'Bitcoin Cash',
          price: '',
          imgurl: '',
          directvol:'',
          totalvol:'',
          marketcap:''
        },
        
      ],
     
      
    }
  }
}
</script>

<style>
.table{
    width: 100%;
}

</style>
