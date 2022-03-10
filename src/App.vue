<template>
<div class="header-wrap">
  <img src="./assets/logo.svg" alt="logo" class="logo">
  <header class="header">
    <nav>
      <router-link to="/">Форма</router-link> 
      <router-link to="/preview">Превью</router-link>
    </nav>
  </header>
</div> 
<div class="line"></div>
<div class="container">
  <router-view/> 
</div>
<footer class="footer">
  all rights reserved
</footer>
</template>

<style>
body,
button {
  font-family: 'Montserrat', sans-serif;
}
.line {
  border-bottom: 1px solid #F1F1F1;
  margin-bottom: 30px;
}
.header-wrap {
  max-width: 1264px;
  display: flex;
  margin: 0 auto;
  align-items: center;  
}
.header {
  margin: 0 auto;
  padding: 24px 0;  
}
.header a {
  color: rgba(17, 17, 17, 0.48);
  text-decoration: none;
  font-size: 14px;
  margin-right: 24px;
}
.header a:last-child {
  margin-right: 0;
}
.logo {
  width: 93px;
  height: 29px;  
  margin-left: 41px;
}
.container {
  max-width: 619px;
  margin: 0 auto;
}
h2 {
  font-size: 16px;
  font-weight: 400;
}
.add-childrens {
  margin: 33px 0 10px 0;
  display: flex;
  justify-content: space-between;
}
.add-childrens button {
  display: flex;
  align-items: center;  
  font-size: 14px;  
  padding: 5px 20px;
  color: #01A7FD;
  border-radius: 100px;
  border: 2px solid #01A7FD;
  text-decoration: none;
  background: none;
}
input {
  border-radius: 4px;
  border: 1px solid #F1F1F1;
}
.text-field_floating {
  position: relative;
  margin-bottom: 10px;
}
.text-field_floating .text-field__input {        
  padding: 1rem .75rem;
  font-size: 14px;
}
.adult .text-field__input  {
  width: 100%;
}
.childrens {
  display: flex;
  justify-content: space-between;
}
.childrens input {
  width: 240px;  
}
.childrens button {
  color: #01A7FD;
  border: none;
  text-decoration: none;
  background: none;
}
.text-field_floating .text-field__label {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  font-size: 13px;
  padding: 1.3rem .75rem;
  pointer-events: none;
  border: 1px solid transparent;
  transform-origin: 0 0;
  transition: opacity .15s ease-in-out, transform .15s ease-in-out;
}
.text-field_floating .text-field__input::-moz-placeholder {
  color: transparent;
}
.text-field_floating .text-field__input::placeholder {
  color: transparent;
}
.text-field_floating .text-field__input:focus,
.text-field_floating .text-field__input:not(:placeholder-shown) {
  padding-top: 1.625rem;     
  padding-bottom: .625rem;
}
.text-field_floating .text-field__input:focus~.text-field__label,
.text-field_floating .text-field__input:not(:placeholder-shown)~.text-field__label {
  opacity: .65;
  transform: scale(.85) translateY(-.75rem) translateX(.15rem);
}
.save-btn {
  margin-top: 20px;
  padding: 10px 20px;
  font-size: 14px;
  border: none;
  background-color: #01A7FD;
  color: white;
  border-radius: 100px;
}
.footer {
  position: absolute;
  background-color: #FAFAFA;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 76px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
