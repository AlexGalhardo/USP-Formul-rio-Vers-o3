<template>
	
	<fieldset id="fieldset_education">

		<h3>Education</h3>

		<label>Academic Education</label><br>

		<span id="errorSchooling">{{ errorSchooling }}</span><br>

		<input type="radio" name="schooling" value="Incomplete High School" id="incompleteHighSchool" @click="hiddenEducationDiv()">  Incomplete High School <br>

		<input type="radio" name="schooling" value="Complete High School" id="completeHighSchool" @click="hiddenEducationDiv()">  Complete High School<br>

		<input type="radio" name="schooling" value="Incomplete University" @click="showEducationDiv()">Incomplete University<br>

		<input type="radio" name="schooling" value="Studying at University" @click="showEducationDiv()">  Studying at University<br>

		<input type="radio" name="schooling" value="Complete University" @click="showEducationDiv()">Complete University Degree<br>

		<input type="radio" name="schooling" value="Complete Master Degree" @click="showEducationDiv()">Complete Master Degree<br>

		<input type="radio" name="schooling" value="Doctorate Degree" @click="showEducationDiv()">Doctorate Degree

		<br><br>

		<div id="div_education" hidden>

			<span id="errorCourseName">{{ errorCourseName }}</span><br>
			<label>Course Name: </label>
			<input type="text" placeholder="Digit your course name" name="courseName" id="courseName"><br><br>

	    <span id="errorInstitutionName">{{ errorInstitutionName }}</span><br>
			<label>Institution Name: </label>
			<input type="text" placeholder="Digit your institution name" name="institutionName" id="institutionName"><br><br>

		</div>

		<span id="errorGraduate">{{ errorGraduate }}</span>
		<label for="date-graduate">Date Graduate: </label>
		<input type="date" name="date-graduate"
		min="2005-01-01" max="2018-12-31" id="graduate">
	    
	  <br><br>

		<input class="input_verify_forms" type="submit" @click="verifyEducation()" value="Verify Education Forms">

		<br><br>

	</fieldset>

</template>



<script>
/* eslint-disable */
export default {
  name: 'education',
  data () {
  	return {
  		errorSchooling: '',
  		errorCourseName: '',
  		errorInstitutionName: '',
  		errorGraduate: ''
  	}
  },
  methods: {
  	showEducationDiv(){
  		if(!document.getElementById("incompleteHighSchool").checked && 
         !document.getElementById("completeHighSchool").checked){

         document.getElementById("div_education").removeAttribute("hidden");
      }
  	},
  	hiddenEducationDiv(){
      document.getElementById("div_education").setAttribute("hidden", "true");
  	},
  	verifyIfElementRadioEducationIsChecked(){
  		let radioSchoolingChecked = false;
      for(let i = 0; i < document.getElementsByName("schooling").length; i++){
        if(document.getElementsByName("schooling")[i].checked){
            radioSchoolingChecked = true;
            break;
        }
      }
      if(!radioSchoolingChecked){
         this.errorSchooling = "You need to choose a option below!";
      } else this.errorSchooling = "";
    },
    getSchoolingValue(){
        for(let i = 0; i < document.getElementsByName("schooling").length; i++){
            if(document.getElementsByName("schooling")[i].checked){
                return document.getElementsByName("schooling")[i].value;
            }
        }
    },
    verifyIfCourseNameHasValue(){
      if(document.getElementById("courseName").value == ""){
        this.errorCourseName = "You need to enter your course name!";
      } else this.errorCourseName = "";
    },
    verifyIfGraduateIsChecked(){
    	var newDate = new Date(document.getElementById("graduate").value);
    	var month = newDate.getMonth();
      var day   = newDate.getDate();  
      var year  = newDate.getFullYear();

      if(newDate.value === ''){
        this.errorGraduate = "You need to check some option below!";
      } else this.errorGraduate = "";
    },
    verifyIfInstitutionNameHasValue(){
      if(document.getElementById("institutionName").value == ""){
        this.errorInstitutionName = "You need to enter a institution name!";
      } else this.errorInstitutionName = "";
    },
    stringifyAndStorageEducationFieldsetValues(){ 
    	let schoolingValue;
      const objectFieldEducationValues = {
          schooling: schoolingValue,  
          graduate: document.getElementById("graduate").value.value,
          courseName: document.getElementById("courseName").value,
          institutionName: document.getElementById("institutionName").value
      }
      const EducationValuesJSON = JSON.stringify(objectFieldEducationValues);
      localStorage.setItem("EducationValuesJSON", EducationValuesJSON);
    },
  	verifyEducation(){
  		this.verifyIfElementRadioEducationIsChecked();
  		this.verifyIfCourseNameHasValue();
  		this.verifyIfGraduateIsChecked();
  		this.verifyIfInstitutionNameHasValue();
  		this.stringifyAndStorageEducationFieldsetValues();
  	}
  }
}
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


