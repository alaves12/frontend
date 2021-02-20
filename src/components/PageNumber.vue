<template>
    <nav class="d-flex justify-content-center" aria-label="...">
        <ul class="pagination">
            <li class="page-item">
            <button class="page-link" @click="page-=1">Previous</button>
            </li>

            <div v-for="(p, index) in pagelist" :key="index">
                <li :class="pageclass[index]"><input type="button" class="page-link" @click="pageclick($event)" :value="p"></li>
            </div>

            <li class="page-item">
            <button class="page-link" @click="page+=1">Next</button>
            </li>
        </ul>
</nav>
</template>

<script>
export default {
    props: {
        pagelist:{
            type:Array,
            required:false
        }
    },
    name:'PageNumber',
    data(){
        return{
            page:1,
            //pageclass:["page-item","page-item","page-item"]
        }
    },
    methods:{
        pageclick(e){
            this.page = e.target.defaultValue;
        }

    },
    computed:{
        pageclass:function(){
            let classlist = ["page-item","page-item","page-item"];
            let last = this.pagelist.slice(-1)[0];
            if(this.page<1){
                this.page=1;
                classlist[0] = "page-item active";
            } else if(this.page>last){
                this.page=last;
                classlist[last-1] = "page-item active";
            }else{
                classlist[this.page-1] = "page-item active";
            }
            this.$emit('movepage', this.page);
            return classlist
        }
    }
}
</script>