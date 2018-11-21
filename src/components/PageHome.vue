<template>

  <div class="page-home">

    <personal-data @verifica="verificaCampos()"></personal-data>
    <br>
    <address-data></address-data>
    <br>
    <job-interest></job-interest>
    <br>
    <education></education>
    <br>
    <professional-experience></professional-experience>
    <br><br><br>
    
  </div>

</template>

<script>
import PersonalData from './PersonalData.vue'
import AddressData from './AddressData.vue'
import JobInterest from './JobInterest.vue'
import Education from './Education.vue'
import ProfessionalExperience from './ProfessionalExperience.vue'

export default {
  name: 'page-home',
  components: {
    PersonalData,
    AddressData,
    JobInterest,
    Education,
    ProfessionalExperience
  }
}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.page-home {
  max-width: 800px; 
  margin: 0 auto;
}
</style>
