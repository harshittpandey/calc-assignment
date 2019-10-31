<template>
  <div class="buttons">
    
    <div class="buttonPannel">
      <div class="button" @click="checkNum(7)">
        7
      </div>
      <div class="button" @click="checkNum(8)">
        8
      </div>
      <div class="button" @click="checkNum(9)">
        9
      </div>
      <div class="button" @click="checkNum('/')">
        /
      </div>
    </div>
    <div class="buttonPannel">
      <div class="button" @click="checkNum(4)">
        4
      </div>
      <div class="button" @click="checkNum(5)">
        5
      </div>
      <div class="button" @click="checkNum(6)">
        6
      </div>
      <div class="button" @click="checkNum('*')">
        *
      </div>
    </div>
    <div class="buttonPannel">
      <div class="button" @click="checkNum(1)">
        1
      </div>
      <div class="button" @click="checkNum(2)">
        2
      </div>
      <div class="button" @click="checkNum(3)">
        3
      </div>
      <div class="button" @click="checkNum('-')">
        -
      </div>
    </div>
    <div class="buttonPannel">
      <div class="button" @click="checkNum(0)">
        0
      </div>
      <div class="button" @click="checkNum('.')">
        .
      </div>
      <div class="button" style="background: red; color: white" @click="checkNum('c')">
        C
      </div>
      <div class="button" @click="checkNum('+')">
        +
      </div>
    </div>
    <div class="buttonPannel">
      <div class="button" style="background: forestgreen; color: white" @click="checkNum('=')" >
        =
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Buttons',
  props: {
  },
  data() {
    return {
    }
  },
  methods: {
    checkNum: function(val) {
      this.$emit("val", val)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.buttons {
  margin: 0 auto;
  width: 300px;
}

.buttonPannel {
  display: flex;
  justify-content: space-between;
  background: #2d2d2d
}

.button {
  background: grey; 
  width: 100%;
  padding: 5px;
  margin: 5px ;
  border-radius: 5px;
  cursor: pointer;
}
</style>
