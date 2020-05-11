<template>
    <div>
        <new-meeting-form v-if="showNewMeetingForm" @added="addNewMeeting($event)"></new-meeting-form>
        <button v-else @click="displayNewMeetingForm">Dodaj nowe spotkanie</button>
        <meetings-list :meetings="meetings" :username="user" @enrollToMeeting="addUserToTheMeeting($event)" @delete="DeleteThisMeeting($event)"
                       @leaveMeeting="removeUserFromMeeting($event)"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";
    export default {
        props: ["user"],
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: [],
                showNewMeetingForm: false
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
                this.showNewMeetingForm = false;
            },
            displayNewMeetingForm() {
                this.showNewMeetingForm = true;
            },
            addUserToTheMeeting(meeting) {
                meeting.participants.push(this.user);
            },
            DeleteThisMeeting(meeting) {
                this.meetings.splice(this.meetings.indexOf(meeting), 1);
            },
            removeUserFromMeeting(meeting) {
                meeting.participants.splice(meeting.participants.indexOf(this.user), 1)
            }
        }
    }
</script>