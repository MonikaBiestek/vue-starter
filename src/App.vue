<template>
<<<<<<< HEAD
    <div>
        <h1>System do zapisów na zajęcia</h1>
        <div v-if="authenticatedUsername">
        	<user-panel :username="authenticatedUsername" @logout="logMeOut()"></user-panel>           
        </div>

        <div v-if="!authenticatedUsername">
        	<login-form @login="logMeIn($event)"></login-form>
        </div>
	<meetings-page v-show="authenticatedUsername" :authenticatedUsername="authenticatedUsername"></meetings-page>
    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import UserPanel from "./UserPanel";
    import MeetingsPage from "./meetings/MeetingsPage";
    export default {
        components: {LoginForm, MeetingsPage, UserPanel},
        data() {
            return {
                authenticatedUsername: '',
            }
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;
            },
            logMeOut() {
                this.authenticatedUsername = '';
            }
        }
    }
</script>
=======
  <div id="app">
	<h1>Witaj w systemie zapisów na zajęcia</h1>
	
	<div v-if="authenticatedUsername">
	<h3>Zalogowany jako: {{authenticatedUsername}}</h3>
	<a @click="logMeOut()">Wyloguj</a>
	</div>
	
	<div v-else>
	    <login-form @login="logMeIn($event)"
		button-label="Zaloguj się"></login-form>
		
	</div>
	
	

	
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
export default {
	components: {LoginForm},
	data() {
		return {
		authenticatedUsername: ''
		};
	},
	methods: {
	logMeIn(username) {
	this.authenticatedUsername=username;
    }, 
	logMeOut() {
	this.authenticatedUsername='';
}
	
}
}
</script>

<style>

</style>
>>>>>>> 28a4ab7e8b8fd5e880edf11b318c296275406216
