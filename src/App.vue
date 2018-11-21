<template>
  <div id="app">
    <header>
      <h1>Welcome Candidate</h1>
      <br>
      <h2>Please Enter Your Data</h2>
      <br>
    </header>

    <page-home></page-home>

    <h4>
      <a href="https://www.icmc.usp.br/">ICMC USP 2018</a>
      <br><br>
      © 2018 <a href="https://galhardoo.com">Alex Galhardo</a>
      <br><br>
      Version 3.0
      <br>
      <br>
      <a href="https://github.com/AlexGalhardo/forms.galhardoo.com-version3">Site made with VueJS 3.0 & Single File Components & Web Components</a>
    </h4>

  </div>

</template>


<!-- SCRIPTS -->
<script>
import PageHome from './components/PageHome.vue'

export default {
  name: 'app',
  components: {
    PageHome
  }
}
</script>



<!-- STYLES -->
<style>
body {
  font-family: "Rubik";
}

header {
  text-align: center;
}

h3, h4 {
  text-align: center;
}

fieldset {
  margin: 5px auto;
  border: none;
  border-radius: 5px;
}

span {
  color: red;
}

a {
  text-decoration: none;
  color: blue;
}

input {
  border: 1px solid #eee;;
  padding: 10px;
  margin: 5px;
}

label {
  font-weight: bold;
}

textarea {
  border-color: #eee;
  border-radius: 5px;
  margin: 10px 0px;
}

textarea:focus {
  border-color: green;
}

input:focus {
  border-color: black;
}

a:hover {
  color: orange;
}

h1 {
  text-align: center;
}

table {
  border-color: white;
}

th, a {
  text-align: center;
  border-color: white;
  margin: 2px 2px;
}

td {
  text-align: center;
  padding: 0.2em;
}

fieldset h3 {
  padding: 10px;
  border-radius: 5px;
  border: 1px solid gray;
  background-color: #eee;
}
</style>
