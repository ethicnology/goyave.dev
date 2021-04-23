<template>
<div >
  
<table style="width:100%">
  <tr>
    <td>
      <img src="/undraw_code_typing_7jnv.svg" width="300">
        <h2>Clean Code</h2>
        <p>Goyave has an expressive, elegant syntax, a robust structure and conventions. Minimalist calls and reduced redundancy are among the Goyave's core principles.</p>
    </td>
    <td>
      <img src="/undraw_speed_test_wxl0.svg" width="275">
        <h2>Fast Development</h2>
        <p>Develop faster and concentrate on the business logic of your application thanks to the many helpers and built-in functions.</p>
    </td>
    <td>
      <img src="/undraw_upgrade_06a0.svg" width="275">
        <h2>Powerful functionalities</h2>
        <p>Goyave is accessible, yet powerful. The framework includes routing, request parsing, validation, localization, testing, authentication, and more!</p>
    </td>
  </tr>
</table>
<!--div align="center">
  <div class="contener_slideshow">
    <div class="contener_slide">
      <div class="slid_1">
        <img src="/undraw_code_typing_7jnv.svg" width="300">
        <h2>Clean Code</h2>
        <p>Goyave has an expressive, elegant syntax, a robust structure and conventions. Minimalist calls and reduced redundancy are among the Goyave's core principles.</p>
      </div>
      <div class="slid_2">
        <img src="/undraw_speed_test_wxl0.svg" width="275">
        <h2>Fast Development</h2>
        <p>Develop faster and concentrate on the business logic of your application thanks to the many helpers and built-in functions.</p>
      </div>
      <div class="slid_3">
        <img src="/undraw_upgrade_06a0.svg" width="275">
        <h2>Powerful functionalities</h2>
        <p>Goyave is accessible, yet powerful. The framework includes routing, request parsing, validation, localization, testing, authentication, and more!</p>
      </div>
    </div>
  </div>
</div-->




<p class="awesomeTitle">Features tour</p>
<ul class="tab">
  <li><a href="#London" class="tablinks active" v-on:click="greet($event, 'London')">Basics</a></li>
  <li><a href="#Paris" class="tablinks" v-on:click="greet($event, 'Paris')">Hello world</a></li>
  <li><a href="javascript:void();" class="tablinks" v-on:click="greet($event, 'Tokyo')">Configuration</a></li>
  <li><a href="javascript:void();" class="tablinks" v-on:click="greet($event, 'Tokyo')">More config</a></li>
  <li><a href="javascript:void();" class="tablinks" v-on:click="greet($event, 'Tokyo')">Other</a></li>
</ul>

<div id="London" class="tabcontent">
  <h3>London</h3>
  <p>London is the capital city of England.</p>
  <pre>
    <code>
    </code>
  </pre>
</div>

<div id="Paris" class="tabcontent">
  <h3>Paris</h3>
  <p>Paris is the capital of France.</p>
</div>

<div id="Tokyo" class="tabcontent">
  <h3>Tokyo</h3>
  <p>Tokyo is the capital of Japan.</p>
</div>

</div>
</template>

<script>
export default {
    name: "Test",
     methods: {
      greet: function openCity(evt, cityName) {
          var i, tabcontent, tablinks;
          tabcontent = document.getElementsByClassName("tabcontent");
          for (i = 0; i < tabcontent.length; i++) {
              tabcontent[i].style.display = "none";
          }
          tablinks = document.getElementsByClassName("tablinks");
          for (i = 0; i < tablinks.length; i++) {
              tablinks[i].className = tablinks[i].className.replace(" active", "");
          }
          document.getElementById(cityName).style.display = "block";
          evt.currentTarget.className += " active";
      }
  }
}
</script>

<style lang="stylus">

table{
  align:center;
  border-collapse: collapse; 
  border: none !important;
}

table, tr, td {
    border: none;
}

td {
  text-align: center;
  vertical-align: middle;
  padding: 10px 20px;
  /*box-shadow: 7px 10px 15px rgba(0, 0, 0, .4);*/
}

.contener_slideshow
{
  width:610px;
  height:400px;
  overflow: hidden;
  position: relative;
}
.slid_1, .slid_2, .slid_3
{
  position: absolute;
  width:610px;
  height:211px;
}
.slid_1{left: 0;}
.slid_2{left: 610px;}
.slid_3{left: 1220px;}
.contener_slide
{
  width: 1220px;
  height: 211px;
  left:0px;
  position: absolute;
  -webkit-animation-duration: 15s;
  -webkit-animation-iteration-count:infinite;
  -webkit-animation-name: anim_slide;
  -moz-animation-duration: 15s;
  -moz-animation-iteration-count:infinite;
  -moz-animation-name: anim_slide;
  -ms-animation-duration: 15s;
  -ms-animation-iteration-count:infinite;
  -ms-animation-name: anim_slide;
  animation-duration: 15s;
  animation-iteration-count:infinite;
  animation-name: anim_slide;
}
@-webkit-keyframes anim_slide 
{
  0% {left:0px;}
  22% {left:0px;}
  33% {left:-610px;}
  45% {left:-610px;}
  66% {left:-1220px;}
  90% {left:-1220px;}
}
@-moz-keyframes anim_slide 
{
  0% {left:0px;}
  22% {left:0px;}
  33% {left:-610px;}
  45% {left:-610px;}
  66% {left:-1220px;}
  90% {left:-1220px;}
}
@-ms-keyframes anim_slide 
{
  0% {left:0px;}
  22% {left:0px;}
  33% {left:-610px;}
  45% {left:-610px;}
  66% {left:-1220px;}
  90% {left:-1220px;}
}
@keyframes anim_slide 
{
  0% {left:0px;}
  22% {left:0px;}
  33% {left:-610px;}
  45% {left:-610px;}
  66% {left:-1220px;}
  90% {left:-1220px;}
}

.awesomeTitle {font-family: 'Helvetica Neue', sans-serif; font-size: 45px; font-weight: bold; letter-spacing: -1px; line-height: 1; text-align: left; }

.awesomeTitleBis {font-family: 'Helvetica Neue', sans-serif; font-size: 35px; font-weight: bold; letter-spacing: -1px; line-height: 1; text-align: center; }

body {font-family: "Lato", sans-serif;}
*, *::before, *::after {
	box-sizing: border-box;
}

ul.tab {
  list-style-type: none;
  overflow: hidden;
  background-color: #787a7d;
  width:100%;
  height:200px;
  float:none;
  display: flex;
  align-items: center;
  justify-content: center;
  
}

/* Float the list items side by side */
ul.tab li {float: left;}

/* Style the links inside the list items */
ul.tab li a {
    display: inline-block;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    transition: 0.3s;
    font-size: 17px;
    font-family: 'Helvetica Neue', sans-serif;
    
    width:300px;
    border-bottom: 1px solid #ccc;
    background-color: #787a7d;
    
}

/* Change background color of links on hover */
ul.tab li a:hover {
    background-color: #8c90ab;
}

/* Create an active/current tablink class */
ul.tab li a:focus, .active {
    background-color: white;
    order-bottom: none;
}

/* Style the tab content */
.tabcontent {
    display: none;
    width:80%;
    padding: 6px 12px;
    height:500px;
    -webkit-animation: fadeEffect 1s;
    animation: fadeEffect 1s;
}

div[class*="tabcontent"]:first-of-type {
    display: block;
}
@-webkit-keyframes fadeEffect {
    from {opacity: 0;}
    to {opacity: 1;}
}

@keyframes fadeEffect {
    from {opacity: 0;}
    to {opacity: 1;}
}o {opacity: 1;}

</style>