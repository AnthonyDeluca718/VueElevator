<template>
  <div class="etr-elevator clearfix">

    <div class="etr-elevator__left">
      <elevator-keypad :queue="queue" @newFloor="newFloor"></elevator-keypad>
      <elevator-queue :queue="queue">Yolo</elevator-queue>
    </div>

    <div class="etr-elevator__right">
      <elevator-building :currentFloor="currentFloor"></elevator-building>
    </div>

  </div>
</template>


<script>

import ElevatorBuilding from "./elevator_building.vue";
import ElevatorKeypad from "./elevator_keypad.vue";
import ElevatorQueue from "./elevator_queue.vue";

let EtrElevator = {
  data() {
    return {
      queue: [],
      currentFloor: 1
    }
  },
  mounted() {
    this.loopUpdate();
  },
  components: {
    'elevator-queue': ElevatorQueue, 'elevator-keypad': ElevatorKeypad, 'elevator-building': ElevatorBuilding
  },
  methods: {
    updateState() {

      let currentFloor = this.currentFloor;
      let queue = this.queue;

      let idx = queue.indexOf(currentFloor);
      //if idx > -1 the current floor is in the queue
      if (idx > -1) {
        queue.splice(idx,1);
      }

      if (currentFloor === 1 && queue.length === 0) {
        //no buttons are pressed so the elevator stays at the lobby
      } else if (queue.length === 0) {
        //no buttons are pressed so the elevator begins its descent to the lobby
        currentFloor -= 1;
        queue.push(1);
      } else {
        //the elevator moves toward the first floor in the queue
        let targetFloor = queue[0];
        if (currentFloor > targetFloor) {
          currentFloor -= 1;
        } else {
          currentFloor += 1;
        }
      }

      this.currentFloor = currentFloor;
      this.queue = queue;

      this.loopUpdate();

    }, loopUpdate() {
      let queue = this.queue;

      let paused = false;
      if (queue.includes(this.currentFloor)) {
        paused = true;
      }

      //If the elevator stops we pause for 3 seconds, otherwise 1 second.
      setTimeout(this.updateState.bind(this), paused ? 3000 : 1000);
    },
    newFloor: function(floor) {
      if (this.currentFloor != floor && !this.queue.includes(floor)) {
        this.queue.push(floor)
      }
    }
  }
}
export default EtrElevator;

</script>


<style>

.etr-elevator {
  display: block;
  width: 960px;
  height: 400px;
  margin: 0 auto;
  border: 1px solid black; }

.etr-elevator__left {
  display: block;
  width: 600px;
  float: left;
  background: #F8F9FD; }

.etr-elevator__right {
  display: block;
  width: 360px;
  float: left; }


</style>
