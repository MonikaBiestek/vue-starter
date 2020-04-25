<template>
  <div id="app">
	<h1>Witaj w systemie zapisów na zajęcia</h1>
	
	<div v-if="authenticatedUsername">
	<h3>Zalogowany jako: {{authenticatedUsername}}</h3>
	<a @click="logMeOut()">Wyloguj</a>
	</div>
	
	<div v-else>
		<input type="email" v-model="email">
	    <button @click="logMeIn()">Zaloguj się</button>
	</div>
	
	

	
  </div>
</template>

<script>
import "milligram";
export default {
	data() {
		return {
		email: '',
		authenticatedUsername: ''
		};
	},
	methods: {
	logMeIn() {
	this.authenticatedUsername=this.email;
	this.email='';
    }, 
	logMeOut() {
	this.authenticatedUsername='';
}
	
}
}
</script>

<style>

</style>
