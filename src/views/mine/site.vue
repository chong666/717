<template>
    <div class="siteModel">
        <header class="site-header">
            <router-link :to="{name:'mine'}"><i class="iconfont icon-back"></i></router-link>
            <b>收货地址</b>
            <i class="iconfont icon-home"></i>
        </header>
        <section>
            <ul class="uls">
                <li>
                    <span class="name_phone">岁月如故<b>18310552816</b></span>
                    <small class="site">北京 北京 海淀区</small>
                    <p class="default">
                        <span class="dui"><i class="btns icon iconfont icon-check"></i>设为默认</span>
                        <span class="cancel">
                            <span @click="add"><i class="iconfont icon-send"></i>编辑</span>
                            <span><i class="iconfont icon-apps"></i>删除</span>
                        </span>
                    </p>
                </li>
            </ul>
            <button class="add" @click="add">＋ 新增加地址</button>
        </section>
    </div>
</template>

<script>
    export default {
        data(){
            return {

            }
        },
        methods:{
            // back(){
            //     this.$router.push("main")
            //     // history.go(-1)
            // },
            add(){
                this.$router.push("/address")
            }
        }
    }
</script>

<style scoped>
    .siteModel{
        width:100%;
        height:100%;
        background: #f5f5f5;
    }
    .uls{
        width:100%;
        background: #fff;
    }
    .uls li{
        min-height:2rem;
    }
    .name_phone{
        display:block;
       padding-top:.28rem;
        font-size: .3rem;
        padding-left:.3rem;
    }
    .name_phone b{
        font-weight: normal;
        padding-left:.3rem;
    }
    .site{
        display: block;
        color:#666;
        padding-left:.3rem;
        margin-top:.2rem;
    }
    .default{
        width:100%;
        margin-top:.28rem;
        line-height: .8rem;
        border-top:1px solid #eee;
        padding-left:.3rem;
        display:flex;
        justify-content: space-between;
        padding-right:.2rem;
        color:#666;
    }
     .dui {
         font-size: 14px;
     }
    .dui i{
        display: inline-block;
        font-style:normal;
        width:.5rem;
        height: 0.5rem;
        border-radius:50%;
        margin-right:.2rem;
        border:1px solid #ccc;
        line-height: .5rem;
        text-align: center;
        font-size:.32rem;
        background: red;
        color:#fff;
    }
    .cancel i{
        padding:0 .2rem;
    }

    .add{
        /*width:70%;
        height:.85rem;
        background:red;
        border:none;
        border-radius:.55rem;
        color:#fff;
        font-size:.29rem;
        margin-left: 15%;
        outline: none;*/
        /*margin-top:.8rem;*/
        position: absolute;
        left: 0;
        right: 0;
        width: 70%;
        margin: .8rem auto;
        height: 45px;
        line-height: 45px;
        background: #fc4141;
        color: #fff;
        border: none;
        border-radius: 30px;
        font-size: .28rem;
    }


    /*.head{
        width:100%;
        height:.85rem;
        background: #fff;
        line-height: .85rem;
        display: flex;
        justify-content: space-between;
        padding:0 .3rem;
        border-bottom:1px solid #ccc;
        font-size: 14px;
    }
    .icon-home{
        display: inline-block;
        width:.6rem;
        height: 0.6rem;
        border:1px solid #ccc;
        border-radius:50%;
        text-align: center;
        line-height: .6rem;
        margin-top:5px;
    }*/
    .site-header {
        height: .88rem;
        line-height: .88rem;
        background: #fff;
        display: flex;
        justify-content: space-between;
        border-bottom: 1px solid #eee;
        padding: 0 5%;
        flex-shrink: 0;
        font-size: .22rem;    
    }
    .site-header b{
        font-size: 16px;
        font-weight: normal;
    }
    .icon-home{
        display: inline-block;
        width: .6rem;
        height: .6rem;
        border: 1px solid #ccc;
        border-radius: 50%;
        text-align: center;
        line-height: .6rem;
        margin-top: .14rem;
    }
</style>
