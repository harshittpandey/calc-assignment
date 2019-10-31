<template>
  <div class="home">
    <Screen :screenData="screenData">
    </Screen>  
    <Buttons @val="newVal">
    </Buttons>
  </div>
</template>

<script>
// @ is an alias to /src
import Screen from '@/components/Screen.vue'
import Buttons from '@/components/Buttons.vue'

export default {
  name: 'home',
  components: {
    Screen,
    Buttons
  },
  data() {
    return {
      first: 0,
      second: 0,
      operator: '',
      res: ''
    }
  },
  computed: {
    screenData: function() {
      return this.res!= ''? this.res: this.first+ ' '+ this.operator+ ' '+ this.second; 
    }
  },
  methods: {

    newVal: function(val) {
      if(val === '=') {
        switch(this.operator) {
          case '+': {
            this.res= this.first+ this.second;
            break;
          }
          case '-': {
            this.res= this.first- this.second;
            break;
          }
          case '*': {
            this.res= this.first* this.second;
            break;
          }
          case '/': {
            this.res= this.first/ this.second;
            break;
          }
        }
      }
      else if(val>=0 && val<=9) {
        if(this.operator === '') {
          this.first= this.first*10+ val; 
        }
        else {
          this.second= this.second*10+ val;
        }  
      }
      else {
        this.operator= val
      }
    }
  }
}
</script>

<style lang="css" scoped>
.home {
  background: #2d2d2d;
  width: fit-content;
  padding: 12px;
  margin: 4rem auto;
}
</style>
