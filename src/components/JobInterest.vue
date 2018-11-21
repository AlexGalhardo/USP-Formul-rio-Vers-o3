<template>
	
	<fieldset>

		<h3>Job Interest</h3>

		<span id="errorPostName">{{ errorPostName }}</span><br>
		<label>Post</label>
		<br>

		<input type="radio" value="Front-End Developer" name="post">Front-End Developer
		<br>
		<input type="radio" value="Back-End Developer" name="post">Back-End Developer
		<br>
		<input type="radio" value="FullStack Developer" name="post">FullStack Developer
		<br>
		<input type="radio" value="Data Base Administrator" name="post">Data Base Administrator
		<br>
		<input type="radio" value="Digital Marketing Analist" name="post">Digital Marketing Analist
		<br>
		<input type="radio" value="Designer" name="post">Designer
		<br>
		<input type="radio" value="Human Resources" name="post">Human Resources
		<br>
		<input type="radio" value="Financial administration" name="post">Financial administration
		
		<br><br>

    <span id="errorPostExperience">{{ errorPostExperience }}</span><br>
		<label>Post Experience: </label>
		<br>
		<input type="radio" name="experience" value="Junior"> Junior<br>
		<input type="radio" name="experience" value="Pleno"> Pleno<br>
		<input type="radio" name="experience" value="Senior"> Senior<br>
		<input type="radio" name="experience" value="Yoda Master">  Yoda Master<br>
		
		<br><br>

    <span id="errorInterestRegion">{{ errorInterestRegion }}</span><br>
		<label for="interestRegion">Interest Region:  </label>
		<select name="interestRegion" id="interestRegion">
			<option value=""></option>
			<option value="SP">SP</option>
			<option value="RJ">RJ</option>
			<option value="MG">MG</option>
			<option value="PR">PR</option>
			<option value="SC">SC</option>
			<option value="AC">AC</option>
			<option value="AM">AM</option>
			<option value="RS">RS</option>
		</select>

		<br><br>

    <span id="errorSalaryPretension">{{ errorSalaryPretension }}</span><br>
		<label for="salaryPretension">Salary Pretension: $</label>
		<input name="salaryPretension" id="salaryPretension" type="number" placeholder="Digit a integer number"> / month
        
    <br><br>

		<input class="input_verify_forms" type="submit" @click="verifyJobInterest()" value="Verify Interest Forms">

	</fieldset>

</template>



<script>
/* eslint-disable */
export default {
  name: 'job-interest',
  data() {
  	return {
  		errorPostName: '',
  		errorPostExperience: '',
  		errorInterestRegion: '',
  		errorSalaryPretension: ''
  	}
  },
  methods: {
  	verifyIfPostNameIsChecked(){
        let postNameChecked = false;
        for(let i = 0; i < document.getElementsByName("post").length; i++){
            if(document.getElementsByName("post")[i].checked){
                postNameChecked = true;
                break;
            }
        }
        if(!postNameChecked){
            this.errorPostName = "You need to select a post below!";
        } else this.errorPostName = "";
    },
    verifyIfExperienceIsChecked(){
        let experienceChecked = false;
        for(let i = 0; i < document.getElementsByName("experience").length; i++){
            if(document.getElementsByName("experience")[i].checked){
                experienceChecked = true;
                break;
            }
        }
        if(!experienceChecked){
            this.errorPostExperience = "You need to select a experience below!";
        } else this.errorPostExperience = "";
    },
    verifyIfInterestRegionHasValue(){
        if(document.getElementById("interestRegion").value == ''){
            this.errorInterestRegion = "You need to choose a region interest below!";
        } else this.errorInterestRegion = "";
    },
    verifyIfSalaryPretensionHasValue(){
        if(document.getElementById("salaryPretension").value == ""){
            this.errorSalaryPretension = "You need to enter a salary pretension!";
        } else this.errorSalaryPretension = "";
    },
  	verifyJobInterest() {
  		this.verifyIfPostNameIsChecked();
  		this.verifyIfExperienceIsChecked();
  		this.verifyIfInterestRegionHasValue();
  		this.verifyIfSalaryPretensionHasValue();
  	}
  }
}
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


