<template>
    <div class="mine">
        <header class="mine-header">
            <div class="head-top">
                <i class="icon iconfont icon-settings" @click="go_to_loginOut"></i>
                <p>我的717商城</p>
                <i class="icon iconfont icon-message"></i>
            </div>
            <div class="head-user">
                <img src="../../imgs/未标题-7.png" alt="">
                <p>路飞</p>
            </div>
        </header>
        <main class="mine-main">     
            <div class="my-store">
                <i class="icon iconfont icon-shop"></i>
                <span>我的店铺</span>
                <i class="icon iconfont icon-more">></i>
            </div>
            <ul class="mine-list">
                <li>
                    <i class="icon iconfont icon-list"></i>
                    <p>待付款</p>
                </li>
                <li>
                    <i class="icon iconfont icon-send"></i>
                    <p>待发货</p>
                </li>
                <li>
                    <i class="icon iconfont icon-deliver"></i>
                    <p>待收货</p>
                </li>
                <li>
                    <i class="icon iconfont icon-refund"></i>
                    <p>售后</p>
                </li>
                <li>
                    <router-link :to="{name:'order'}">                  
                        <i class="icon iconfont icon-form"></i>
                        <p>我的订单<i class="icon iconfont icon-more">></i></p>
                    </router-link>
                </li>
            </ul>
            <ul class="mine-mess">

                <li @click="go_to_balance">
                    <i class="icon iconfont icon-pay"></i>
                    <span>账户余额</span>
                    <i class="icon iconfont icon-more">></i>
                </li>

                <li @click="go_to_site">
                    <i class="icon iconfont icon-pay"></i>
                    <span>地址管理</span>
                    <i class="icon iconfont icon-more">></i>
                </li>

                <li>
                    <i class="icon iconfont icon-pay"></i>
                    <span>我的客服</span>
                    <i class="icon iconfont icon-more">></i>
                </li>
            </ul>
            <div class="mine_hot">
                <div class="hot_tit">
                    <p>热门推荐</p>
                </div>
                <div class="hot_main">
                    <dl>                 
                        <dt><img src="../../imgs/food-show04.gif" alt=""></dt>
                       
                        <dd>
                            <p>光临 天然蜂蜜500g 包邮 包邮</p>
                            <span>￥39.00</span>
                            <i class="icon iconfont icon-cart"></i>
                        </dd>
                    </dl>                    
                    <dl>
                        <dt><img src="../../imgs/food-show04.gif" alt=""></dt>
                        <dd>
                            <p>光临 天然蜂蜜500g 包邮 包邮</p>
                            <span>￥39.00</span>
                            <i class="icon iconfont icon-cart"></i>
                        </dd>
                    </dl>
                    <dl>
                        <dt><img src="../../imgs/food-show04.gif" alt=""></dt>
                        <dd>
                            <p>光临 天然蜂蜜500g 包邮 包邮</p>
                            <span>￥39.00</span>
                            <i class="icon iconfont icon-cart"></i>
                        </dd>
                    </dl>
                    <dl>
                        <dt><img src="../../imgs/food-show04.gif" alt=""></dt>
                        <dd>
                            <p>光临 天然蜂蜜500g 包邮 包邮</p>
                            <span>￥39.00</span>
                            <i class="icon iconfont icon-cart"></i>
                        </dd>
                    </dl>
                </div>
            </div>
        </main>
    </div>
</template>
<script>
    import router from '../../routes/router.config'
    export default {
        name:"mine",
        data:function(){
    	    return{

    	    }
        },
        methods:{
    	    go_to_loginOut(){
    	  	    this.$router.push('/loginOut')
    	    },
            go_to_site(){
                this.$router.push('/site')
            },
            go_to_balance(){
                this.$router.push('/balance')
            },
        },
        beforeRouteEnter: (to, from, next) => {
            //router.push('/login');
            next();
        },
        mounted(){
            // console.log(this.$route)
        }
    }
</script>
<style scoped>
    .mine{
        width: 100%;
        height: 100%;
        display: -webkit-flex;
        -webkit-flex-direction: column;
        box-sizing: border-box;
    }
    .mine-header{
        background: url('../../imgs/未标题-3.png') no-repeat;
        background-size: 100% 100%;
    }
    .mine .head-top{
        height: 50px;
        line-height: 50px;
        display: flex;
        position: relative;
        color: #fff;
    }
    .mine .head-top .iconfont{
        width: 15%;
        text-align: center;
        font-size: 18px;
    }
    .mine .head-top p{
        flex: 1;
        text-align: center;
        font-size: 18px;
    }
    .mine .head-user{
        text-align: center;
    }
    .mine .head-user img{
        width: 60px;
        height: 60px;
    }
    .mine .head-user p{
        color: #fff;
        margin: 10px 0;
        font-size: 14px;
    }

    .mine .mine-main{
        -webkit-flex: 1;
        overflow-y: scroll;
        background: #f3f3f3;
    }
    .mine .my-store{
        background: #fff;
        height: 70px;
        line-height: 70px;
        color: #fc4141;
        font-size: 18px;
        padding-left: 5%;
        border-bottom: 1px solid #f1f1f1;   
        position: relative;
    }
    .mine .my-store .icon-shop{
        font-size: 24px;
    }
    .mine .my-store .icon-more{
        position: absolute;
        right: 5%;
        font-size: 18px;
    }
    .mine .mine-list{
        background: #fff;
        display: flex;
        padding: 12px 1%;
        border-bottom: 1px solid #f1f1f1;
    }
    .mine .mine-list li{
        flex: 1;
        text-align: center;
        color: #666;
    }
    .mine .mine-list li:last-child{
        border-left: 1px solid #f1f1f1;
    }
    .mine .mine-list li .icon{
        font-size: 24px;
    }
    .mine .mine-list li p{
        font-size: 12px;
    }
    .mine .mine-list li .icon-more{
        font-size: 12px;
    }

    .mine .mine-mess{
        background: #fff;
        margin-top: 10px;
    }
    .mine .mine-mess li{
        height: 60px;
        line-height: 60px;
        border-top: 1px solid #f1f1f1;
        padding-left: 5%;
        color: #666;
        position: relative;
    }
    .mine .mine-mess li .icon{
        font-size: 20px;
    }
    .mine .mine-mess li span{
        font-size: 14px;
    }
    .mine .mine-mess li .icon-more{
        font-size: 16px;
        position: absolute;
        right: 5%;
    }
    .mine_hot{
        width: 100%;
        margin-top: 10px;
    }
    .hot_tit{
        text-align: center;
        padding: 10px 0;
        background: #fff;
    }
    .hot_main{
        width: 100%;
        height: auto;
        display: flex;
        flex-wrap:wrap;
    }
    .hot_main dl{
         width: 48%;
        height: 200px;
        margin-left: 2%;
        background: #fff;
        margin-bottom: 5px;       
    } 
    .hot_main dl dt{
        width:90%;
        height:120px;
    }
    .hot_main dl dt img{
        width: 100%;
        height: 100%;
        margin-left: 5%;
    }
    .hot_main dl dd p{
        height: 36px;
        overflow: hidden;
        padding:0px 10px;
        color: #000;
    }
    .hot_main dl dd span{
        color: red;
        margin-left: 5px;
    }
    .hot_main dl dd i{
        color: red;
        margin-left: 50%;
    }

    a{
        color: #666;
    }
</style>
