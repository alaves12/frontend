<template>
  <div class="card">
  <div class="card-body">
    <h4 class="card-title">CALC</h4>
      <div class="card-text">
        <p>answer: {{answer}}</p>
        <hr>
        <p>Formula:</p>
        <hr>
        <p>
          <textarea name="example" cols="70" rows="10" v-model="formula"></textarea>
        </p>
      </div>
    <input type="button" class="btn btn-primary" value="calculate" @click="calculate">
    <p>{{formula}}</p>
  </div>
</div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'CalcInput',
  props: {
    formobj:{
      type:Array,
      default:[],
      required:false
    }

  },
  data() {
    return{
      answer: '',
      formula: '',
      count: 0,
      formlist: []
    }
  },
  methods: {
     calculate(){
      this.formlist = this.formobj;
      console.log(this.formula.split('\n'));
      let arr = this.formula.split('\n');
      let newarr = [];
      let fn = '';
      let formarr = {"definition":'', "formula":'', "value":0}
      for (let n in arr){
          if (arr[n] != ""){
            newarr.push(arr[n]);
          }
      }
      for (let k in newarr){
          if (k!=newarr.length-1){
          fn += newarr[k].trim() + ';';
          formarr.definition += newarr[k].trim() + ';';
          }
          else{
            fn += 'return '+newarr[k]+';';
            formarr.formula = newarr[k];
        }
      }
      function CalcEval(obj){
        return Function(obj)();
      }
      this.answer = CalcEval(fn);
      formarr.value = this.answer;
      this.formlist.push(formarr)

      this.$emit(`calculate`, this.answer);
      this.$emit('Showtable', this.formlist);
    }
  }
  
}
</script>