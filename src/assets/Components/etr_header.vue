<template>
  <div class="etr-header clearfix">
    <div class="etr-header__left">
      <slot name="name"></slot>
    </div>

    <div class="etr-header__right">
      <slot name="description"></slot>
    </div>
  </div>
</template>


<script>

  let EtrHeader = {
  }

  export default EtrHeader;

</script>

<style>

.etr-header {
  display: block;
  margin: 20px auto;
  width: 930px;
  padding: 15px;
  background: #F8F9FD;
  border-radius: 8px;
  border: 1px solid black; }

.etr-header__left {
  float: left; }

.etr-header__right {
  float: right;
  text-align: right; }

</style>
