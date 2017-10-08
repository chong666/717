<template>
	<div class="shop">
		<header class="head">
			<i class="iconfont icon-back"></i>
			<b>购物车</b>
			<span>
				编辑
				<i class="iconfont icon-message"></i>
			</span>
		</header>

		<div class="main">
			<div class="cart_main">
				<div class="empt_box" v-if="if_has_items">
					<div class="empt_imgs"><img src="../../imgs/未标题-7.png" alt=""></div>
					<p>购物车为空</p>
					<span>去逛逛</span>
				</div>

				<div class="shop_list" v-else>
					<item-comp v-for="x in cart_list" :info="x" :key="x.id"></item-comp>
				</div>
			</div>

			<div class="hot_list">
				热门推荐
			</div>
			<div class="bottom">
				到底了噢！
			</div>
		</div>
		
		<footer class="cart-footer">
            <div class="cart-footer-allxuan">
                <div class="btns icon iconfont" :class="{'icon-check':check_all}" @click="selected_all"></div>
                <span>全选</span>
            </div>
            <div class="cart-footer-total">
                <p class="total">合计：<span class="total-num">￥{{get_selected}}</span></p>
                <p class="freight">(运费：<span>￥0.00</span>)</p>
            </div>
            <button class="balance">结算</button>
        </footer>

	</div>
</template>
<script>
import {mapState,mapGetters} from 'vuex'
import item from './item.vue'
	export default {
		data() {
			return {
	      		if_has_items:true,
	      		check_all:false
			}
		},
		created() {

	  	},
	  	components:{
	    	"item-comp":item
	  	},
	  	computed:{
	    	...mapState(['cart_list']),
	    	...mapGetters(['get_selected'])
	  	},
	  	methods:{
	    	selected_all(){
	      		this.check_all = !this.check_all;
	      		this.$store.commit('check_all',this.check_all);
	      		console.log(this.$store.state.cart_list)
	    	}
	  	},
	  	mounted(){
	    	if(this.cart_list.length>0){
	      		this.if_has_items = false
	    	}
	  	}
	}
</script>
<style scoped>
	.shop {
		background: #f5f5f5;
	  display:flex;
	 flex-direction: column;
	 width:100%;
	 height:100%;

	}

	.head {
		width: 100%;
		height: 0.88rem;
		line-height: 0.88rem;
		display: flex;
		justify-content: space-between;
		border-bottom: 1px solid #eee;
		padding: 0 8px;
		text-align: center;
		flex-shrink: 0;
		font-size: 0.22rem;
	  
	}

	.head span i {
		padding-left: 10px;
	}

	.head b {
		padding-left: 28px;
		font-size: 16px;
		font-weight: normal;
	}

	.main {
		width: 100%;
	  	flex:1;
		overflow: hidden;
		overflow-y: auto;
	}

	.bottom {
		width: 100%;
		height: .7rem;
		line-height: .8rem;
		font-size: 0.3rem;
		color: #666;
		text-align: center;
	}

	.empt_box {
		width: 100%;
		height: 6.2rem;
		display: flex;
		justify-content: center;
		align-items: center;
		background: #fff;
		flex-direction: column;
		margin-bottom:10px;
	}

	.empt_imgs {
		width: 1.36rem;
		height: 1.36rem;
	}

	.empt_imgs img {
		display: block;
		width: 100%;
		border-radius: 50%
	}
	.empt_box span{
		border:1px solid red;
		padding:5px 8px;
		margin-top:8px;
		border-radius:5px;
		color:red
	}
	.empt_box p{
		line-height: 30px;
		color:#666;
	}


	.cart-footer{
        display: flex;
        height: 55px;
        padding-left: 12px;
        color: #555;
        background: #fff;
    }
    .cart-footer-allxuan{
        width: 35%;
        font-size: 14px;
        display: flex;
    }
    .cart-footer-allxuan .btns{
        margin-top: 15px;
        margin-right: 5px;
    }
    .cart-footer-allxuan span{
    	flex: 1;
    	line-height: 60px;
    	font-size: 14px;
    }
    .cart-footer-total{
        flex: 1;
        text-align: center;
        margin-top: 5px;
    }
    .cart-footer-total .total{
        font-size: 14px;
    }
    .cart-footer-total .total-num{
        color: tomato;
    }
    .cart-footer .balance{
        width: 35%;
        border: none;
        background: tomato;
        color: #fff;
        font-size: 14px;
    }
	
	.hot_list{
		font-size: 14px;
		margin-left: 10px;
		color: #555;
	}

	.btns {
		width: 0.45rem;
		height: 0.45rem;
		font-size: 0.3rem;
		line-height: 0.42rem;
		border: solid 0.02rem #cccccc;
		border-radius: 50%;
		overflow: hidden;
		text-align: center;
		color: #fff;
		margin-right: 0.12rem;
	}
	.icon-check {
		background: #fc4141;
	}
</style>
