<template>
	
	<fieldset id="fieldset_professional_experience">

		<h3>Professional Experiences</h3>

		<input type="radio" name="hasExperience" value="Has Professional Experience" id="hasExperience"@click="showButtonAddProfessionalExperience()"> Has Professional Experience
		
		<input type="radio" name="hasExperience" value="Doesn't Has Professional Experience" id="doesNotHasExperience" @click="hiddenButtonAddProfessionalExperience()" checked> Doesn't Has Professional Experience

		<div id="button_add_professional_exp" hidden>
			<br><br>
			<input @click="showDivAddExperienceData()" type="button" value="Add Professional Experience">
		</div>
		
		<div id="div_has_professional_exp" hidden>

			<br><br>

			<hr>

			<span id="errorCompanyName">{{ errorCompanyName }}</span><br>
			<label>Company Name:</label>
			<input type="text" placeholder="Digit company name" id="companyName" name="companyName">
			<br><br>

			<label>Start:  </label>
			<input type="date" id="start" name="trip-start"
       min="2005-01-01" max="2018-12-31">

			<br><br>
			<strong>End:  </strong>
			<input type="date" id="start" name="trip-start"
       min="2005-01-01" max="2018-12-31">

			<br><br>
			<span id="errorBusinessSegment">{{ errorBusinessSegment }}</span><br>
			<label>Business Segment</label>:<br>
			<input type="radio" value="Tecnologia e Informática" name="businessSegment">  Technology <br>
			<input type="radio" value="Human Resources" name="businessSegment">  Human Resources <br>
			<input type="radio" value="Varejo de Produtos Físicos" name="businessSegment">  Retail of Physical Products <br>
			<input type="radio" value="Marketing Digital" name="businessSegment">  Digital Marketing <br>
			<input type="radio" value="Food Trade" name="businessSegment">  Food Trade <br>
			<input type="radio" value="Entertainment" name="businessSegment">  Entertainment <br>
			<input type="radio" value="General Services" name="businessSegment">  General Services

			<br><br>
			<span id="errorPositionHeld">{{ errorPositionHeld }}</span><br>
			<label>Position Held:</label>
			<input type="text" placeholder="Digit your position held in this experience" id="positionHeld" name="positionHeld"><br><br>

			<span id="errorJobResponsabilities">{{ errorJobResponsabilities }}</span><br>
			<label>Enter your main duties and responsibilities in the position held: </label><br>
			<textarea rows="10" cols="70" name="jobResponsabilities" id="jobResponsabilities"></textarea>
			<br><br>
			<input type="submit" @click="hiddenButtonAddExperinceData()" value="Delete This Experience">

			<hr>

			<input class="input_verify_forms" type="submit" @click="verifyProfessionalExperience()" value="Verify Professional Forms">

		</div>

	</fieldset>

</template>



<script>
/* eslint-disable */
export default {
  name: 'professional-experience',
  data() {
  	return {
  		errorCompanyName: '',
  		errorBusinessSegment: '',
  		errorPositionHeld: '',
  		errorJobResponsabilities: ''
  	}
  },
  methods: {
  	showButtonAddProfessionalExperience(){
        if(document.getElementById("hasExperience").checked){
            document.getElementById("button_add_professional_exp").removeAttribute("hidden");
        } 
    },
    hiddenButtonAddProfessionalExperience(){
        if(document.getElementById("doesNotHasExperience").checked){
            document.getElementById("button_add_professional_exp").setAttribute("hidden", "true");
        }
    },
    hiddenButtonAddExperinceData(){
        document.getElementById("div_has_professional_exp").setAttribute("hidden", "true");
    },
    showDivAddExperienceData(){
        document.getElementById("div_has_professional_exp").removeAttribute("hidden");
    },
  	verifyProfessionalExperience(){
  		// company name
  		if(document.getElementById("companyName").value == ''){
          this.errorCompanyName = "You need enter the name of the last company you worked in";
      } else this.errorCompanyName = "";

 			// position held
      if(document.getElementById("positionHeld").value == ''){
          this.errorPositionHeld = "You need to enter a position held!";
      } else this.errorPositionHeld = "";

      // business segment
      let businessSegmentChecked = false;
      for(let i = 0; i < document.getElementsByName("businessSegment").length; i++){
          if(document.getElementsByName("businessSegment").checked){
              businessSegmentChecked = true;
              break;
          }
      }
      if(!businessSegmentChecked){
          this.errorBusinessSegment = "You need to choose one option below!";
      } else this.errorBusinessSegment = "";

      // job responsabilities
      if(document.getElementById("jobResponsabilities").value == ''){
          this.errorJobResponsabilities = "Please tell us a little more about your duties and responsibilities for the last position held."
      } else if(document.getElementById("jobResponsabilities").value.toString().length < 50){
          this.errorJobResponsabilities = "Enter a answer with at least 50 characters!"
      } else this.errorJobResponsabilities = "";
  	}
  }
}
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


