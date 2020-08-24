<template>
  <div class="calculator">
    <div class="display">{{current || '0'}}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="devide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator">×</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      previous:null,
      current:'',
      operator:null,
      operatorclicked:false,
    }
  },
  methods:{
    clear() {
      this.current='';
    },
    sign()  {
      this.current = this.current.charAt(0) === '-' ? //如果current第0個是-的話,會被加上負號
        this.current.slice(1) : `-${this.current}`; //${}會等於串聯,- + this current
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(number)  {
      if(this.operatorclicked){
        this.current='';
        this.operatorclicked=false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if(this.current.indexOf('.') === -1){ //indexof 如果裡面沒有 . 就會回傳-1 為了不要太多點
        this.append('.');
      }
    },
    setprevious() {
      this.previous = this.current;
      this.operatorclicked = true;
    },
    devide()  {
      this.operator = (a, b) => a / b; //(a,b) => a / b = function(a,b){ return a/b;} 箭頭函數
      this.setprevious();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setprevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setprevious();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setprevious();
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.current)
        )}`;
        this.previous = null
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator{
  width: 270px;
  margin: auto;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(50px , auto);
}
.display{
  grid-column: 1/5;
  background-color:#333;
  color:white;
}
.zero{
  grid-column: 1/3;
}
.btn{
  background-color: #f2f2f2;
  border: 1px solid #999;
}

.operator{
  background-color:orange;
  color:white;
}
</style>
