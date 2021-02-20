<template>
  <div class="home">
    <div class="row">
      <div class="col-lg-3"></div>
      <div class="col-lg-6">
      <CalcInput :formobj="formarr" @calculate = "answer = $event" @Showtable = "formarr = $event"></CalcInput>
      <br>
      <Mytable :formobj="formarr"></Mytable>
      <button  class="btn btn-primary" @click="deleteform">Delete</button>
      </div>
      <div class="col-lg-3"></div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import CalcInput from '@/components/CalcInput.vue'
import Mytable from '@/components/Mytable.vue'


export default {
  name: 'Home',
  components: {
    HelloWorld,
    CalcInput,
    Mytable
  },
  data() {
    return {
      answer : 0,
      formarr :[],
    }
  },
  methods: {
    deleteform(){
      this.formarr = [];
    }
  }
}
</script>
