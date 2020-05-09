<template>

    <form @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input  type="text" v-model="newMeeting.name"/>
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <button > Dodaj </button> <p style="display:inline-block; color:red;" v-if="error && submitting" >Spotkanie musi mieć nazwę!</p>  
    </form>
</template>

<script>
    export default {
        data() {
            return {
              newMeeting: {
				name: '',
				description: '',
				participants: []
			  },
              submitting: false,
              error: false,
	
             }
        },
        methods: {
            addNewMeeting() {			    
			    this.submitting = true
				this.clearStatus()

				if (this.invalidName) {
				this.error = true
				return
				}
                this.$emit('added', this.newMeeting);
                this.newMeeting = {};
				this.error = false
				this.submitting = false
            },
			clearStatus() {
			this.error = false
        }
        },				
		computed: {
            invalidName() {
            return this.newMeeting.name ===''
            },
		}
    }
</script>
<style>
</style>
