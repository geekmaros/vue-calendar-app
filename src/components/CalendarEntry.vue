<template>
	<div id="calendar-entry">
      <div class="calendar-entry-note">
        <p v-if="error" style="color: red; font-size: 13px">{{ errorMessage }}</p>
        <input type="text" v-model="inputEntry" placeholder="New Event" required />
        <p class="calendar-entry-day">Day of event: <span class="bold">{{ titleOfActiveDay }}</span></p>
        <a class="button is-primary is-small is-outlined" @click="submitEvent(inputEntry)">Submit</a>
      </div>
    </div>
</template>

<script>
import {store} from "../store.js";
export default {

  name: 'CalendarEntry',

  data() {
    return {
      inputEntry : "",
      errorMessage : "Field Can\'t be empty",
      error: false

    };
  },
  methods:{
    submitEvent(eventDetails){
      if (this.inputEntry.length > 0) {
        store.submitEvent(eventDetails);
      this.inputEntry=""; 
      this.error = false
      }
      else{
        this.error = true;

      }
      
    }

  },
  computed:{
  	titleOfActiveDay(){
  		return store.getActiveDay().fullTitle;
  	}
  }
};
</script>

<style lang="css" scoped>
</style>
