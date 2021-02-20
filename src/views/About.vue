<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div class="row">
    <div class="col-lg-2"></div>
    <div class="col-lg-8">
    <br>
    <MyGoods :goods="goods"></MyGoods>
    <br>
    <PageNumber :pagelist="pages" @movepage="page=$event;getgoods();"></PageNumber>
    <!-- <button @click="showcount()"></button> -->
    </div>
    <div class="col-lg-2"></div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import MyGoods from '@/components/MyGoods.vue'
import PageNumber  from '@/components/PageNumber.vue'
export default {
  components:{
      MyGoods,
      PageNumber,
  },
  data(){
    return{
      goods:[],
      goodsurl:'http://localhost:8000/goods/?page=',
      count:[],
      pages:[],
      page:1,
    }
  },
  async created(){
    await this.getgoods();
    this.pages = this.count;
  },

  methods:{
    async getgoods(){
      try{
        let url = this.goodsurl+this.page;
        console.log(url)
        const res = await axios.get(url);
        let countlist = [];
        for(let i=1;i<res.data.count/10+1;i++){  
          countlist.push(i);
        };
        this.count = countlist.map(e => {return e})
        this.goods = res.data.results;
      } catch(error){
        console.log(error);
      }
    },
    showcount(){
      console.log(this.count)
    }
    
  }
}
</script>
