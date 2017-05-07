<template>
  <div class="etr-elevator__queue">
    {{"Queue of floors we will stop at: " + this.queueString}}
  </div>
</template>

<script>


let ElevatorQueue = {
  props: ['queue'],
  computed: {
    queueString() {
      return this.queue.join(" ")
    }
  }
}

export default ElevatorQueue;

</script>


<style>

.etr-elevator__queue {
  display: flex;
  height: 80px;
  background: #F8F9FD;
  font-size: 20px;
  align-items: center;
  font-family: sans-serif; }

</style>
