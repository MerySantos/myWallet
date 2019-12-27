<template>
  <div id="app">
    <div>
      <b-container >
        <b-row>
          <b-col cols="8" offset-md="2">
            <h2> My Cards</h2> 

            <b-container v-for="(card, index) of cards" :key="index">
              <itemCard  :dataCard="card"></itemCard>
            </b-container>
          </b-col>
        </b-row>
        <b-row>
          <b-button variant="link">Add new card</b-button>

          <b-button v-b-toggle.collapse-3 class="m-1">Toggle Collapse</b-button>
          <b-collapse visible id="collapse-3">
            <addCard></addCard>  
          </b-collapse>
        </b-row>
      </b-container>
    </div>
  </div>
</template>



<script>
import itemCard from './components/itemCard.vue'
import addCard from './components/addCard.vue'

export default {
  name: 'app',
  components: {
    itemCard,
    addCard
  },
  data(){
    return{
      cards:[
        {isDefault:true, typeCard:"Visa",nameCard:"123456789112", exDate:"10/2023"}
      ]
    }
  },
  methods:{

  }
}


</script>

<style>
*{
  outline:1px solid red;
}
#app {
  font-family: 'Open-Sans', "Roboto", Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px ;
}


</style>
