<template>
  <div class="lightDiv"></div>
</template>

<script>
export default {
  name: 'Test',
  props: {
    msg: String
  }
}
</script>

<style>
.lightDiv{
  height: 50px;
  width: 50px;
  border-radius: 50%;
  border: black 1px solid;
  margin-bottom: 5px;
}
</style>
