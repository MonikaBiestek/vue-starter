<template>
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
