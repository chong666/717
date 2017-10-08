<template>
    <div class="List">
        <header class="list-header">
            <input type="text" placeholder="搜索你想找的商品" @focus="go_to_search">
            <img src="../../imgs/xiaoxi.png" alt="">
        </header>

        <main class="list-main">
            <ul>
                <li v-for="(x,i) in catagory_list" :key="i">
                    <router-link :to="{name:'catagory',params:{index:i}}">{{x.title}}</router-link>
                </li>

            </ul>
            <div class="list-food">
                <div class="list-food-show" v-for="i in catagory_content"  :key="i.id">
                    <router-link :to="{name:'shop'}" tag="span"> 
                        <img :src="i.pic" alt="">
                        <p>{{i.name}}</p>
                    </router-link>
                </div>

            </div>
            <masker-layer :isActive="masker_active"></masker-layer>
        </main>
  </div>
</template>
<script>
import masker from '../../components/loading.vue';
export default {
  data() {
	  return {
		  masker_active: true,
		  catagory_list:[],
		  catagory_content:[]
	  }
  },
  watch:{
	  "$route":function(n,o){
		  let idx = n.params.index;
		  if(this.catagory_list[idx])this.catagory_content = [...this.catagory_list[idx].items]
	  }
  },
  computed:{

  },
  methods:{
	  go_to_search:function(){
		 this.$router.push({name:'search'})
	  }
  },
  components: {
	  "masker-layer": masker
  },
  created() {
	  this.$http.post('/h5/mtop.relationrecommend.wirelessrecommend.recommend').then((res)=> {
		  this.catagory_list = [...res.data.data.result[0].moduleList];
		  this.catagory_content = [...this.catagory_list[0].items]
		  this.masker_active = false
	  })
  }
}
</script>
<style scoped>
    .wrap{
        font-size: 12px;
        display: -webkit-flex;
        -webkit-flex-direction: column;
    }
    .list-header{
        height: 50px;
        display: flex;
        position: relative;
        padding-right: 5%;
        border-bottom: 1px solid #f1f1f1;
    }
    .list-header input{
        flex: 1;
        height: 30px;
        margin-top: 10px;
        background: #F5F5F5;
        border: none;
        border-radius: 5px;
        text-align: center;
        margin-left: 10%;
    }
    .list-header img{
        width: 22px;
        height: 22px;
        margin-top: 14px;
        margin-left: 5%;
    }

    .list-main{
        -webkit-flex: 1;
        overflow-y: scroll;
        display: flex;
        /*margin-top: 50px;*/
    }
    .list-main ul{
        width: 30%;  
    }
    .list-main ul li{
        height: 40px;
        line-height: 40px;
        text-align: center;
        background: #f1f1f1;
    }
    .list-main ul li a{
        font-weight: normal;
        text-decoration: none;
        color: #888;
        display: block;
    }
    .list-main ul li .active{
        background: #fff;
        color: tomato;
        border-left: 2px solid tomato;
    }
    .list-main .list-food{
        flex: 1;
        margin-left: 1%;
        padding-top: 1%;
    }
    .list-main .list-food .list-food-show{
        float: left;
        width: 30%;
        text-align: center;
        background: #f6f6f6;
        margin: 1%;
        padding: 5px 5px 5px 0;
    }
    .list-main .list-food .list-food-show img{
        width: 64px;
        height: 38px;
    }
    .list-main .list-food .list-food-show p{
        line-height: 50px;
    }
</style>
