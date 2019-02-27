<template>
	<div class="day column" @click="setActiveDay(day.id)">
          <div class="day-banner has-text-white has-text-centered">{{ day.abbvTitle }}</div>
          <div class="day-details">
            <div class="day-number">{{day.id}}</div>
     		<CalendarEvent :day="day" v-for="(event, index) in day.events"
     		:event="event"/>
          </div>
        </div>
</template>

<script>
import CalendarEvent from "./CalendarEvent.vue";
import {store} from "../store.js";

export default {

  name: 'CalendarDay',

  data() {
    return {

    };
  },
  methods:{
  	setActiveDay(dayId){
  		return store.setActiveDay(dayId);
  	}
  },
  props:['day'],
  components:{
  	CalendarEvent

  }
};
</script>

<style lang="css" scoped>
</style>
