<template>
    <q-layout view="lHh lpr lFf">
      <q-header elevated>
        <q-toolbar>
          <q-toolbar-title>
            Project Reiss
          </q-toolbar-title>
        </q-toolbar>
      </q-header>
      <q-page-container>
      <q-page padding>
    <div  class="row">
      <div class="col-xs-auto col-sm-12 col-md-9">
        <div class="column ">
      <div class="col ">
        <coinchart />
      </div>
      <div class="col">
       <coindetails />
      </div>
    </div>
      </div>
      <div class="col-xs-auto col-sm-12 col-md-3">
             <pricecompare />
      </div>

    </div>
      </q-page>
      </q-page-container>
 
    </q-layout>
</template>





<script>
import pricecompare from '../components/pricecompare'
import coindetails from '../components/coindetails'
import coinchart from '../components/coinchart'


export default {
  name: 'MyLayout',

  components: {
    pricecompare,
    coindetails,
    coinchart
     },
  data () {
    return {
      
      }
  },
  methods: {
  }
}
</script>

<style>
</style>
