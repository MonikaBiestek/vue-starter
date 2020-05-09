<template>
    <div>       
	   <button v-if="visible" @click="hide">Dodaj nowe spotkanie</button>
       <new-meeting-form v-if="visible1" @added="addNewMeeting($event)"></new-meeting-form>
       <meetings-list :user="this.authenticatedUsername" :meetings="meetings" @delete:meeting="deleteMeeting" @add:participant="addParticipant($event)"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";
    

    export default {
        components: {NewMeetingForm, MeetingsList},
	props: ['authenticatedUsername'],

        data() {
            return {
                meetings: [],
				user: this.authenticatedUsername,
                visible: true,
		        visible1: false,
		
            };
        },
        methods: {
            addNewMeeting(meeting) {		
				this.meetings.push(meeting);
				this.visible1=!this.visible1
				this.visible=!this.visible
            },
			
            hide(event) {
				this.visible=!this.visible
				this.visible1=!this.visible1	
            },
			
            deleteMeeting(name) {
				this.meetings = this.meetings.filter(
				meeting=> meeting.name !== name
				)
            },
		}
	}
			
			

			
			
			
			
    
</script>
