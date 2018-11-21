<template>

	<fieldset>

		<h3>Personal Data</h3>

		<span id="errorCompleteName">{{ errorCompleteName }}</span><br>
		<label for="completeName">Name: </label>
		<input type="text" id="completeName" name="name" placeholder="Digit your complete name">
		<br><br>

		<span id="errorEmail">{{ errorEmail }}</span><br>
		<label for="email">Email: </label><input name="email" type="email" placeholder="Digit your email" id="email"><br><br>

		<span id="errorCellphone">{{ errorCellphone }}</span><br>
		<label for="cellphone">Cellphone: </label><input name="cellphone" type="number" placeholder="Digit your cellphone" id="cellphone"><br><br>

		<label>Gender: </label><br>
		<span id="errorGender">{{ errorGender }}</span><br>
		<input type="radio" name="gender" value="Male"> Male<br>
		<input type="radio" name="gender" value="Female"> Female<br>
		<input type="radio" name="gender" value="Other"> Other
		
		<br><br>

		<span id="errorMaritalStatus">{{ errorMaritalStatus }}</span><br>
		<label>Marital Status: </label>
		<select name="maritalStatus" id="maritalStatus">
			<option value=""></option>
			<option value="Single">Single</option>
			<option value="Married">Married</option>
			<option value="Divorced">Divorced</option>
			<option value="Dating">Dating</option>
			<option value="Widower">Widower</option>
		</select>
		
		<br><br>

    <span id="errorNationality">{{ errorNationality }}</span><br>
		<label>Nationality: </label>
		<select name="nationality" id="nationality">
			<option value=""></option>
			<option value="Brazil">Brazil</option>
			<option value="Americano">American</option>
			<option value="Spain">Spain</option>
			<option value="England">England</option>
			<option value="Argentina">Argentina</option>
			<option value="Mexico">Mexico</option>
			<option value="Russia">Russia</option>
			<option value="India">India</option>
			<option value="France">France</option>
			<option value="Italy">Italy</option>
			<option value="Germany">Germany</option>
			<option value="Canada">Canada</option>
		</select>

		<br><br>
		
		<span id="errorNumberID">{{ errorNumberID }}</span><br>
		<label for="numberID">NumberID: </label>
		<input type="number" name="numberID" placeholder="Enter your number ID" id="numberID" max="11">
	  <br><br>
    <input class="input_verify_forms" type="submit" @click="verifyPersonalData()" value="Verify Personal Forms">

	</fieldset>

</template>



<script>
/* eslint-disable */
export default {
  name: 'personal-data',
  data () {
    return {
  	  errorCompleteName: '',
  	  errorEmail: '',
  	  errorCellphone: '',
  	  errorGender: '',
  	  errorMaritalStatus: '',
    	errorNationality: '',
    	errorNumberID: '',
    }
  },
  methods: {
  	verifyName() {
      if(document.getElementById("completeName").value === ''){
        this.errorCompleteName = "Digit a valid name!";
      } else {
      	this.errorCompleteName = "";
      }
  	},
  	verifyEmail() {
      if(document.getElementById("email").value == ''){
          this.errorEmail = "You need to enter a email!";
        } else if (document.getElementById("email").value != ''){
          /**
           * Reference: http://jsfiddle.net/ghvj4gy9/embedded/result,js/
           */
          var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

          if(!re.test(String(document.getElementById("email").value).toLowerCase())){
              this.errorEmail = "Enter a valid email!";
          } else {
              this.errorEmail = "";
          }
        }else {
          this.errorEmail = "";
        }
  	},
  	verifyIfCellphoneHasValue() {
        if(document.getElementById("cellphone").value == ''){
            this.errorCellphone = "You need to enter a cellphone number!";
        } else {
            this.errorCellphone = "";
        }
    },
    verifyIfGenderIsChecked() {
        let genderChecked = false;
        for(let i = 0; i < document.getElementsByName("gender").length; i++){
            if(document.getElementsByName("gender")[i].checked){
                genderChecked = true;
                break;
            }
        }

        if(!genderChecked){
            this.errorGender = "You need to check a gender below!";
        } else {
            this.errorGender = "";
        }
    },
    verifyIfMaritalStatusIsSelected() {
        if(document.getElementsByName("maritalStatus").value == ''){
            this.errorMaritalStatus = "You need to select a marital status below!";
        } else {
            this.errorMaritalStatus = "";
        }
    },
    verifyIfNationalityWasSelected() {
        if(document.getElementById("nationality").value == ''){
            this.errorNationality = "You need to select a nationality below!";
        } else {
            this.errorNationality = "";
        }
    },
    verifyIfNumberIDHasValue() {
        if(document.getElementById("numberID").value == ''){
            this.errorNumberID = "You need to enter your number ID!";
        } 
        else if (document.getElementById("numberID").value.toString().length < 11 
                  || 
                  document.getElementById("numberID").value.toString().length > 11){

            this.errorNumberID = "You need digit a valid numberID with at least 11 characters!";
        
        } else {
            this.errorNumberID = "";
        }
    },
    verifyPersonalData() {
    	this.verifyName();
    	this.verifyEmail();
    	this.verifyIfCellphoneHasValue();
    	this.verifyIfGenderIsChecked();
    	this.verifyIfMaritalStatusIsSelected();
    	this.verifyIfNationalityWasSelected();
    	this.verifyIfNumberIDHasValue();
    }
  }
}
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


