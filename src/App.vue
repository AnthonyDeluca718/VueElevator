<template>
  <div>
    <etr-header>
      <div slot="name" >Anthony Deluca</div>
      <div slot="description" >Expand the Room Elevator Challenge in Vue</div>
    </etr-header>
    <etr-elevator></etr-elevator>
  </div>
</template>

<script>

import EtrHeader from "./assets/components/etr_header.vue";
import EtrElevator from "./assets/components/etr_elevator.vue"

export default {
  components: {
    'etr-header': EtrHeader,
    'etr-elevator': EtrElevator
  }
}

</script>


<style>

body {
  margin: 0px;}

.clearfix:after {
  content: " ";
  visibility: hidden;
  display: block;
  height: 0;
  clear: both; }

</style>
