<template>
  <div class="etr-elevator__building">
    <div v-for="floor in buildingFloors" :class="floor.classname">
      {{floor.text}}
    </div>
  </div>
</template>

<script>

let ElevatorBuilding = {
  props: ['currentFloor'],
  computed: {
    buildingFloors() {
      let floors = [];
      for(let i=10; i > 0; i--) {
        let floor = {};

        let extraClass = "";
        if (i === this.currentFloor) {
          extraClass = " etr-elevator__building__floor--currentFloor";
        }
        floor.classname = "etr-elevator__building__floor" + extraClass;

        let prefix = "th";
        if (i === 2) {
          prefix = "nd";
        } else if (i === 3) {
          prefix = "rd";
        }

        floor.text = `${i}${prefix} floor`;

        floors.push(floor);
      }
      return floors;
    }
  }

}

export default ElevatorBuilding;

</script>


<style>

.etr-elevator__building {
  background: cyan; }

.etr-elevator__building__floor {
  display: flex;
  margin: 0 auto;
  height: 40px;
  width: 160px;
  justify-content: center;
  align-items: center;
  font-size: 20px;
  background: #cd853f; }

.etr-elevator__building__floor--currentFloor {
  background: red; }

</style>
