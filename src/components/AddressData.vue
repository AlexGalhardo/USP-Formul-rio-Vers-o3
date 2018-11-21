<template>
	
	<fieldset>

		<h3>Address Data</h3>

		<span id="errorStreet">{{ errorStreet }}</span><br>
		<label for="street">Street: </label>
		<input type="text" name="street" id="street" placeholder="Digit your street"><br><br>
		
		<span id="errorNeighborhood">{{ errorNeighborhood }}</span><br>
		<label for="neighborhood">Neighborhood: </label>
		<input type="text" name="neighborhood" id="neighborhood" placeholder="Digit your neighborhood"><br><br>
		
		<span id="errorResidenceNumber">{{ errorResidenceNumber }}</span><br>
		<label for="residenceNumber">Residence Number: </label>
		<input type="number" name="residenceNumber" id="residenceNumber" placeholder="Digit your residence number">

		<br><br>

		<input class="input_verify_forms" type="submit" @click="verifyAddressData()" value="Verify Address Forms">

	</fieldset>

</template>



<script>
/* eslint-disable */
export default {
  name: 'address-data',
  data () {
  	return {
  		errorStreet: '',
  		errorNeighborhood: '',
  		errorResidenceNumber: '',
  	}
  },
  methods: {
  	verifyIfStreetHasValue(){
        if(document.getElementById("street").value == ''){
            this.errorStreet = "You need to enter a street name!";
        } else this.errorStreet = "";
    },
    verifyIfNeighborhoodHasValue(){
        if(document.getElementById("neighborhood").value == ''){
            this.errorNeighborhood= "You need enter a neighborhood name!";
        } else this.errorNeighborhood = "";
    },
    verifyIfResidenceNumberHasValue(){
        if(document.getElementById("residenceNumber").value == ''){
            this.errorResidenceNumber = "You need to enter a residence number!";
        } else this.errorResidenceNumber = "";
    },
  	verifyAddressData(){
  		this.verifyIfStreetHasValue();
  		this.verifyIfNeighborhoodHasValue();
  		this.verifyIfResidenceNumberHasValue();
  	}
  }
}
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


