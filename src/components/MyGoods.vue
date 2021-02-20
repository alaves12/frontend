<template>
    <table class="table">
  <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Price</th>
      <th>Remarks</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(obj, index) in goods" :key="index">
        <td>{{obj.id}}</td>
        <td>{{obj.name}}</td>
        <td>{{obj.shop_price}}</td>
        <td>{{obj.goods_brief}}</td>
    </tr>
  </tbody>
</table>
    
</template>

<script>

export default {
    name:'MyGoods',
    props:{
        goods:{
            type:Array,
            default:[],
            required:false
        }
    },

}
</script>