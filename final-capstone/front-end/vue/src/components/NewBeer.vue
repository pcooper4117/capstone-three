<template>
<div class='new-beer'>
<div id="NewBeerForm">

<form> 
    <p> ID: </p>
    <input type="text" v-model="newBeer.obdb_id"> <br>
    <p> Beer Name: </p>
    <input type="text" v-model="newBeer.name"> <br>
    <p> Beer Brewery: </p>
    <input type="text" v-model="newBeer.brewery"> <br>
    <p> Description: </p>
    <input type="text" v-model="newBeer.description"> <br>
    <p> Image: </p>
    <input type="text" v-model="newBeer.image"><br>
    <p> ABV: </p>
    <input type="text" v-model="newBeer.abv"><br>
    <p> Type: </p>
    <input type="text" v-model="newBeer.type"><br>
    <p> Active (Y/N): </p>
    <input type="text" v-model="newBeer.active"><br>

    <input type="button" value="Add Beer" v-on:click="addBeer()" />
 </form>

</div>
</div>
</template>

<script>

import beerService from '../services/BeerService';

export default {
  data() {
    return {
       newBeer: {
        obdb_id: "",
        name: "",
        brewery: "",
        description: "",
        image: "",
        abv: "",
        type: "",
        active: ""
       }
    };
  },
  methods: {
    addBeer(){
      beerService.addBeer(this.newBeer).then(response => {  // send the API response to a function 
      if(response.status === 201) { // if post was successful (HTTP status 201)
          this.$router.push("/")
      }
    })
    }
  }
}


</script>

<style scoped>
.NewBeerForm {
    display: grid;
    grid-template-columns: 1fr 1fr;
}


</style>