<template>
    <div class="list_b">
        <div class="btns icon iconfont" :class="{'icon-check':selected}" @click="select_fn"></div>
        <dl class="cart-show">
            <dt><img :src="info.url" alt=""></dt>
            <dd>
                <p class="cart-show-title">{{info.name}}</p>
                <p class="cart-show-cheng">×{{item_count}}</p>
                <p class="cart-price">￥<span>{{info.price}}</span></p>
                <div class="cart-change">
                    <p class="cart-price-jian" @click="minus">-</p>
                    <p class="cart-price-num">{{item_count}}</p>
                    <p class="cart-price-jia" @click="add">+</p>
                </div>
            </dd>
        </dl>
    </div>
</template>
<script>

    export default {
        props: ['info','select_all'],
        data() {
            return {
                selected: false,
                item_count:1
            }
        },
        created(){
            //this.selected = this.$store.
        },
        methods: {
            select_fn(idx) {
                this.selected = !this.selected;
            },
            add(){
                this.item_count++;
                this.$store.commit('change_count',[this.info.id,this.item_count])
                
            },
            minus(){
                this.item_count--;
                this.$store.commit('change_count',[this.info.id,this.item_count])
            }
        },
        watch:{
            select_all:function(n){
                this.selected = n;
            },
            selected:function(n){
                this.$store.commit('selected_item',[this.info.id,n])
            }
        },
        mounted(){
            this.item_count = this.info.count
        }
    }
</script>
<style scoped>

	.list_b{
        display: flex;
        background: #fff;
        margin-bottom: 10px;
        padding: 12px;
        height: 120px;
        position: relative;
    }

    .list_b dl{
        margin-left: 30px;
        display: flex;
    }
    .list_b dt{
        width: 100px;
        height: auto;
        padding: 15px 5px;
        border: 1px solid #ccc;
    }
    .list_b dt img{
        width: 100%;
        height: 100%;
    }
    .list_b dd{
        flex: 1;
        margin-left: 10px;
    }
    .list_b dd .cart-show-title{
        font-size: 12px;
        color: #666;
    }
    .list_b dd .cart-show-cheng{
        position: absolute;
        bottom: 35px;
        font-size: 14px;
    }
    .list_b dd .cart-price{
        color: red;
        position: absolute;
        bottom: 10px;
    }
    .list_b dd .cart-price span{
        font-size: 16px;
    }
    .list_b dd .cart-change{
        position: absolute;
        right: 12px;
        bottom: 12px;
        display: flex;
    }
    .cart-price-jian,.cart-price-jia{
        width: 25px;
        height: 25px;
        line-height: 25px;
        text-align: center;
        font-size: 16px;
        border: 1px solid #ccc;
    } 
    .cart-price-jian{
        border-radius: 5px 0 0 5px;
    }
    .cart-price-jia{
        border-radius: 0 5px 5px 0;
    }
    .cart-price-num{
        width: 40px;
        height: 25px;
        line-height: 25px;
        text-align: center;
        font-size: 16px;
        border: 1px solid #ccc;
    }

	.btns {
		width: 25px;
		height: 25px;
		font-size: 14px;
		line-height: 25px;
		border:  1px solid #ccc;
		border-radius: 50%;
		overflow: hidden;
		text-align: center;
		color: #fff;
		position: absolute;
        top: 0;
        bottom: 0;
        left: 10px;
        margin: auto;
	}
	.icon-check {
		background: #fc4141;
	}
</style>
