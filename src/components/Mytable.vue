<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                <th>Definition</th>
                <th>Formula</th>
                <th>Answer</th>
                </tr>
            </thead>
             <tbody>
                <tr v-for="(result,index) in formobj" :key="index"> 
                    <td>{{result.definition}}</td>
                    <td>{{result.formula}}</td>
                    <td>{{result.value}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name:'Mytable',
    props: {
    formobj: {
      type: Array,
      default: [],
      required: false
    }
    }
}
</script>