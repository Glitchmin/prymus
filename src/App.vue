<template>
  <div id="container-fluid">
    <nav class="navbar navbar-light bg-light">
      <span class="navbar-text">
        Participants list
      </span>
    </nav>
    <h1> List</h1>
    <div v-if="participants.length > 0">
        <div v-for="participant in participants" v-bind:key="participant.id">
          {{participant.name}} {{participant.surname}}
		  <div2 v-if="participant.name[participant.name.length-1]=='a'">
			<button type="button" class="btn btn-info">kobiet się nie bije</button>
		  </div2>
		  <div2 v-else>
			<button v-on:click="deleteParticipant(participant)" type="button" class="btn btn-danger">Kill him!</button>
		  </div2>
		</div>
	</div>
    <div v-else class="alert alert-dark" role="alert">
      Nothing's here :C
    </div>
    <form>
      <h1>Add Participant</h1>
      <div class="form-group">
        <label for="participant-name">Name</label>
        <input class="form-control" id="participant-name" placeholder="Enter name" v-model="newParticipantName">
      </div>
      <div class="form-group">
        <label for="participant-last-name">Last name</label>
        <input class="form-control" id="participant-last-name"  placeholder="Enter last name" v-model="newParticipantsurname">
      </div>
      <button type="submit" class="btn btn-primary" v-on:click.prevent="addParticipant()">Submit</button>

    </form>
  </div>

</template>

<script>
  export default {
  data: function (){
    return {
      participants: [],
      newParticipantName: null,
      newParticipantsurname: null,
    }
  },
  methods: {
    addParticipant: function(){
      var newParticipant = { name: this.newParticipantName, surname: this.newParticipantsurname };
    newParticipant.id = Math.random();
      this.participants.push(newParticipant);
      this.newParticipantName = null;
      this.newParticipantsurname = null;
    },
    deleteParticipant: function(participant){
      this.participants = this.participants.filter((added) => added.id !== participant.id);
    }
  }
}
</script>

<style>
	.container-fluid{
		padding: 0;
		marging: 0;
	}
</style>