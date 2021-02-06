<template>
  <div class="home">
    <div class="row">
      <div class="col-lg-3"></div>
      <div class="col-lg-6">
      <CalcInput @calculate = "answer = $event" @Showtable = "formarr = $event"></CalcInput>
      <Mytable :definition="formarr.definition" :formula="formarr.formula" :answer="formarr.value"></Mytable>
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
      formarr :{},
    }
  }
}
</script>
