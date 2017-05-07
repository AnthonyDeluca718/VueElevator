<template>
  <div class="etr-elevator__keypad">
    <div v-for="(key, index) in keypadArr">
      <div :class="key.classname" @click="sendFloor(index+1)">{{key.text}}</div>
    </div>
  </div>
</template>

<script>

let ElevatorKeypad = {
  props: ['queue'],
  methods: {
    sendFloor: function(floor) {
      this.$emit("newFloor", floor);
    }
  },
  computed: {
    keypadArr() {
      let keypadArr = [];
      for (let floor=1; floor<=10; floor++) {
        let key = {};
        let extraClass = "";
        if ( this.queue.includes(floor) ) {
          extraClass = " etr-elevator__keypad__key--pressed";
        }
        key.classname = "etr-elevator__keypad__key" + extraClass;
        key.text = String.fromCharCode(9311+floor);

        keypadArr.push(key);
      }

      return keypadArr;
    }
  }
}

export default ElevatorKeypad;

</script>


<style>

.etr-elevator__keypad {
  display: block;
  height: 160px;
  margin: 80px 100px;
  background: #f5f5dc; }

.etr-elevator__keypad__key {
  display: flex;
  height: 80px;
  width: 80px;
  float: left;
  justify-content: center;
  align-items: center;
  font-size: 40px; }

.etr-elevator__keypad__key:hover {
  background: cyan; }

.etr-elevator__keypad__key--pressed {
  background: red; }

  .etr-elevator__keypad__key--pressed:hover {
    background: red; }


</style>
