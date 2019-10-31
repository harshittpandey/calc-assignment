<template>
  <div class="home" style="">
    <!-- <div style="color: white">
      first{{first}}
      operator {{operator}}
      second {{second}}
      res {{res}}
    </div> -->
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
      first: '',
      second: '',
      operator: '',
      res: 0,
      screenData: '0',
      isFloat: false,
      allowedKeys: ['+', '-', '/', '*', '.', "Enter", 'Escape']
    }
  },
  computed: {
  },
  methods: {
    initialize: function() {
      this.first= '';
      this.second= '';
      this.res= '';
      this.operator= '';
      this.screenData= '0';
      this.isFloat= false
    },
    calRes: function() {
      switch(this.operator) {
          case '+': {
            this.res= parseFloat(this.first)+ parseFloat(this.second);
            break;
          }
          case '-': {
            this.res= parseFloat(this.first)- parseFloat(this.second);
            break;
          }
          case '*': {
            this.res= parseFloat(this.first)* parseFloat(this.second);
            break;
          }
          case '/': {
            this.res= parseFloat(this.first)/ parseFloat(this.second);
            break;
          }
      }
      this.screenData= this.res;
      this.first= this.res;
      this.second= '';
      this.operator= '';
    },
    enterVal: function(val) {
        // handling condition when screenData is 0
        if(this.screenData === '0' ) this.screenData= '';
        
        this.screenData+= val.toString();
        if(val>=0 && val<=9) {
        // handling condition when result becomes first operand.
        // if result is 5 and you want to enter 3. then first operand will be 3
          if(this.res!= '') {
            this.screenData= val;
            this.first= '';
            this.res= '';
          }
          if(this.operator === '') this.first+= val;
          else this.second+= val;  
        }
        // checking if it is float value or not
        else if(val === '.') {
          if(this.res!= '') {
            this.screenData= '0.';
            this.first= '0';
            this.res= '';
          }
          if(this.operator === '') {
            this.first+= '.' 
            this.isFloat= true;
          }
          else {
            this.second+= '.' 
            this.isFloat= true;
          }
        }
        // handling operator
        else{
          if(this.second !='') {
            this.calRes();
            this.second= ''
          }
          else {
            this.res= ''
          }
          this.operator= val
          this.isFloat= false;
        }
    },
    newVal: function(val) {
      if(val === 'c') {
        this.initialize();
      }
      else if(val === '=') {
        this.calRes();
      }
      else {
        this.enterVal(val)
      }
    }
  },
  created() {
    window.addEventListener('keydown', (e) => {
      if(e.key>=0 || e.key<=9 || this.allowedKeys.indexOf(e.key)>-1) {
        var key= e.key;
        if(key=='Enter') {
          key='=';
        }
        else if(key=='Escape') {
          key='c';
        }
        this.newVal(key)
      }
    });
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
