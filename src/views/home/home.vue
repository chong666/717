<template>
    <div class="home">
        <header class="home-header">
            <span><img src="../../assets/717.png"></span>
            <input type="text" @focus="go_to_search" placeholder="请输入您要购买的商品">
            <div class="oo">
                <i class="iconfont">&#58998;</i>
                <p>我的店铺</p>
            </div>
            <div class="oo">
                <i class="iconfont">&#59018;</i>
                <p>消息</p>
            </div>
        </header>
        <main class="home-main" @scroll="can_i_query && load_more()" ref="main">
            <div class="main-wrap">
                <div class="swiper-container banner">
                    <div class="swiper-wrapper">
                        <div class="swiper-slide">
                            <img src="../../imgs/home-banner01.png" alt="">
                        </div>
                        <div class="swiper-slide">
                            <img src="../../imgs/home-banner02.png" alt="">
                        </div>
                        <div class="swiper-slide">
                            <img src="../../imgs/home-banner03.png" alt="">
                        </div>
                    </div>
                </div>
                <div class="nav">
                    <ul>                 
                        <li>
                            <img src="../../imgs/home-list01.png" alt="">
                            <p>家乡味道</p>
                        </li>
                        <li>
                            <img src="../../imgs/home-list02.png" alt="">
                            <p>进口食品</p>
                        </li>
                        <li>
                            <img src="../../imgs/home-list03.png" alt="">
                            <p>牛奶乳品</p>
                        </li>
                        <li>
                            <img src="../../imgs/home-list04.png" alt="">
                            <p>茶果冲饮</p>
                        </li>
                    </ul>
                    <ul>                 
                        <li>
                            <img src="../../imgs/home-list05.png" alt="">
                            <p>休闲零食</p>
                        </li>
                        <li>
                            <img src="../../imgs/home-list06.png" alt="">
                            <p>米面粮油</p>
                        </li>
                        <li>
                            <img src="../../imgs/home-list07.png" alt="">
                            <p>调味调料</p>
                        </li>
                        <li>
                            <img src="../../imgs/home-list08.png" alt="">
                            <p>酒水饮料</p>
                        </li>               
                    </ul>
                    <div class="list_txt">
                        <span>商城<br>动态</span>
                        <span>绿色无污染 无公害 无添加 天然有机蔬菜源头吃的放心，健康第一，安全保证，确保蔬菜新鲜</span>
                    </div>
                </div>
                <div class="tiantian">
                    <p class="tian-title"><b>天天特惠</b> 每天都有惊喜</p>
                    <span class="tian-more">更多<i class="icon iconfont">></i></span>
                </div>
                <div class="list-show">
                    <div class="list-left">
                        <img src="../../imgs/daily_fresh.png" alt="">
                    </div>
                    <div class="list-right">
                        <img src="../../imgs/gaodian.png" alt="">
                        <img src="../../imgs/luwei.png" alt="">
                    </div>
                </div>
                <div class="homeBox">
                    <div class="title_n title_ns">
                        <p>———— 家乡的味道 ————</p>
                        <a href="#">更多<i class="icon iconfont">></i></a>
                    </div>
                    <p class="p"></p>
                    <div class="content_home">
                        <good-comp v-for="items in goods_list" :key="items.item_id" :id="items.item_id" :url="items.pic_path" :name="items.title" :price="items.originalPrice" @tips-active="tips_active"></good-comp>
                    </div>
                </div>
                <div class="loading">{{is_finished}}</div>                  

            </div>

        </main>
        <tips-comp :active="active">添加成功</tips-comp>
    </div>
</template>
<script>
import axios from 'axios'
import good from '../../components/good.vue';
import tips from '../../components/tips.vue';
export default {
    name: 'home',
    data() {
        return {
            goods_list: [],
            can_i_query: true,
            channel_id: 1,
            is_finished: 'loading...',
            active: false
        }
    },
    components: {
        "good-comp": good,
        "tips-comp": tips
    },
    created() {
        axios.post('/mall/index/getGoodsChannel', { channel_id: this.channel_id }).then((res) => {
            this.channel_id++;
            this.goods_list = [...res.data.listItem];
        })
    },
    methods: {
        tips_active(data) {
            if (data) {
                this.active = true;
            } else {
                this.active = false;
            }
        },
        go_to_search() {
            this.$router.push('/search');
        },
        load_more() {
            let main = this.$refs.main;
            let total_height = main.querySelector('.main-wrap').offsetHeight;
            let main_height = main.offsetHeight;
            let scroll_top = main.scrollTop;

            if (total_height - scroll_top - main_height < 20) {
                // console.log('到底了')
                this.can_i_query = false;
                axios.post('/mall/index/getGoodsChannel', { channel_id: this.channel_id }).then((res) => {
                    this.channel_id++;
                    this.goods_list = [...this.goods_list, ...res.data.listItem]
                    this.can_i_query = true;
                    if (this.channel_id >= 4) {
                        this.is_finished = '我是有底线的...'
                        this.can_i_query = false;
                    }

                })

            }

        }
    },
    mounted: function(){
        var banner = new Swiper('.banner',{
            autoplay: 1000
        })
    }
}

</script>
<style>
    /*@import url('./swiper/swiper.css');*/
    * {
        margin: 0;
        padding: 0;
        font-size: .22rem;
        font-family: 微软雅黑;
    }

    .home {
        width: 100%;
        height: 100%;
        display: -webkit-flex;
        -webkit-flex-direction: column;
    }

    .home-header {
        width: 100%;
        height: .90rem;
        background: #fff;
        display: -webkit-flex;
        -webkit-justify-content: space-around;
        align-items: center;
        display: flex;
    }

    .home-header input {
        background: #F5F5F5;
        width: 50%;
        height: 60%;
        border: 0;
        text-indent: .5rem;
    }

    .home-header span {
        width: 12%;
        height: 40%;
    }

    .home-header span img {
        width: 100%;
        height: 100%;
    }

    .home-header .oo {
        text-align: center;
        color: #FC4141;
    }

    .home-main{
        -webkit-flex: 1;
        overflow-y: scroll;
        background: #F6F5F5;
    }

    .home-main .banner{
        width: 100%;
    }
    .home-main .banner img{
        width: 100%;
        height: 178px;
    }

    .home-main .nav{
        background: #fff;
        margin-top: 5px;
    }
    .home-main .nav ul{
        display: flex;
    }
    .home-main .nav ul li{
        flex: 1;
        text-align: center;
    }
    .home-main .nav ul li img{
        width: 44px;
        height: 44px;
        margin-top: 8px;
    }
    .home-main .nav ul li p{
        font-size: 12px;
        margin-top: 5px;
        margin-bottom: 5px;
        color: #333;
    }

    .home-main .list_txt{
        width:100%;
        padding-right:10px;
        padding-top: 10px;
        padding-bottom: 10px;
    }
    .home-main .list_txt span:nth-child(1){
        float: left;
        padding: 2px 10px;
        color: #FF6D00;
        font-size: 14px;
    }
    .home-main .list_txt span:nth-child(2){
       display: inline-block;
       padding: 3px 5px;
       width:82%;
       height:46px;
       border:1px solid #ccc;
       border-radius: 8px;
       overflow: hidden;
    }

    .home-main .tiantian{
        width: 100%;
        height: 40px;
        line-height: 40px;
        background: #fff;
        margin-top: 5px;
        padding-left: 10px;
        padding-right: 10px; 
        display: flex;      
        position: relative;
    }
    .home-main .tiantian .tian-title{
        font-size: 12px;
        color: #FF6D00;       
    }
    .home-main .tiantian .tian-title b{
        font-size: 16px;
        margin-right: 5px;
    }
    .home-main .tiantian .tian-more{
        position: absolute;
        right: 10px;
        font-size: 12px;
    }

    .home-main .list-show{
        background: #fff;
        margin-top: 5px;
        width: 100%;
        height: 240px;
        padding-top: 5px;
        padding-bottom: 5px;
        display: flex;
        box-sizing: border-box;
    }
    .home-main .list-show .list-left{
        width: 50%;
    }
    .home-main .list-show .list-left img{
        width: 100%;
        height: 100%;
    }
    .home-main .list-show .list-right{
        flex: 1;
        margin-left: 5px;
    }
    .home-main .list-show .list-right img{
        width: 100%;
        height: 49%;
    }


    .title_n{
        width: 100%;
        height: 44px;
        line-height: 44px; 
        background: #fff;
        display: flex;
        position: relative;
        margin-top: 5px;
    }
    .title_n img{
        width: 30px;
        height: 30px;
        margin-left: 15px;
    }
    .title_n a{
        text-decoration: none;
        position: absolute;
        right: 10px;
        top: 0;
        color: #000;
    }
    .title_ns{
        height: 40px;
    }
    .title_ns p{
        width: 100%;
        text-align: center;
        color: #ff6d00;

    }
    .title_ns img{
        width: 20px;
        height: 20px;
    }
    .p{
        width: 100%;
        height: 3px;
        background:#eeeeee; 
    }
    .coupon{
        width: 100%;
        height: 160px;
        display: flex;
        background: #eeeeee;
    }
    .coupon .coupon-left{
        width: 48%;
        margin-left: 1%;

    }
    .coupon .coupon-left img{
        width: 100%;
        height: 100%;
    }
    .coupon .coupon-right{
        width: 48%;
        margin-left: 2%;
    }
    .coupon .coupon-right img{
        width: 100%;
        height: 48%;
    }
    .content_home{
        width: 100%;
        display: flex;
        flex-wrap:wrap;
    }
    .content_home dl{
        width: 49%;
        height: auto;
        background: #fff;
        margin-left: 1%;
        margin-top: 5px;

    }
    .content_home dl dt{
        width:100%;
        height:120px;
    }
    .content_home dl dt img{
        width: 96%;
        height: 100%;
        margin-left: 2%;
    }
    .content_home dl dd p{
        margin-left: 5px;
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 2;
        overflow: hidden;
    }
    .content_home dl dd span{
         color: red;
         margin-left: 5px;
    }
    .content_home dl dd i{
        color: red;
        margin-left: 50%;
    }

    .loading {
        line-height: 44px;
        text-align: center;
        background: #eee;
    }
</style>