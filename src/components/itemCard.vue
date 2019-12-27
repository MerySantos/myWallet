<template>
  <div class="hello">
    <b-container class="bv-example-row">
      <b-row>
        <b-col>
            <font-awesome-icon :class="{defaultColor:dataCard.isDefault}" icon="check-circle" />
        </b-col>
        <b-col>
          <img :src="imageCard" :alt="dataCard.typeCard" width="70"/> 
        </b-col>
        <b-col>
          <p> {{nameCard}}   
           {{dataCard.nameCard}}</p>
          <span> {{dataCard.exDate}}</span>
        </b-col>
        <b-col>
          <b-container>
          
            <b-row> 
              <b-col>
                <b-button variant="link">Remove</b-button>
              </b-col>

              <b-col>
                <b v-if="dataCard.isDefault" class="textDefaultAction"><span > Default</span></b>
                <template v-else>
                  <b-button variant="link" >Set as default</b-button>
                </template>
              </b-col>

            </b-row>
          </b-container>

        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
// import * from './reusable/cardsBase'

export default {
  name: 'itemCard',
  props:{
    dataCard:Object
  },
  // ['dataCard'] , 
  computed:{
    imageCard() {
      let image = require.context('../assets/', false, /\.svg$/)
      return image( './'+srcImageCard(this.dataCard.typeCard) + ".svg")
    },
    nameCard(){
      return textCard(this.dataCard.typeCard)
    }
  }
  
}


function srcImageCard(typeCard){
  let src="Default card ico"

  switch (String(typeCard)) {
    case "Visa":
      src = "Visa Card Logo";
      break;
    case "Amex":
      src = "Amex Card Logo";
      break;
    case "Master":
      src = "Master Card Logo";
      break;
  }  
  return src
} 

function textCard(typeCard){
  let text=""

  switch (String(typeCard)) {
    case "Visa":
      text = "Visa";
      break;
    case "Amex":
      text = "American Express";
      break;
    case "Master":
      text = "Master Card";
      break;
  }  
  return text
}




</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .defaultColor{
    color:#52d03e
  }

  .textDefaultAction{
    color:#43689e;
    text-decoration:underline;
    padding:6px  }


</style>
