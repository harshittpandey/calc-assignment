<template>
  <div class="screen">
    <b>
      {{screenData}}
    </b>
  </div>
</template>

<script>
export default {
  name: 'Screen',
  props: [
    "screenData"
  ]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.screen {
  width: 300px;
  height: 40px;
  background: grey;
  margin: 0 auto;
  border-radius: 5px;
  margin-bottom: 2rem;
  color: white;
  font-size: 1.5rem;
  text-align: end;
  padding-top: 0.8rem;
}
</style>
