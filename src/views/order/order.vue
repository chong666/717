<template>
	<div class="order">
		<header class="order-header">
			<router-link :to="{name:'mine'}"><i class="iconfont icon-back"></i></router-link>
			<b>我的订单</b>
			<div class="order-header-mess">			
				<img src="../../imgs/xiaoxi.png" alt="">
			</div>
		</header>
		<main class="order-main">
			<ul class="order-switch">
				<li class="li1">全部</li>
				<li>待付款</li>
				<li>待发货</li>
				<li>待收货</li>
				<li>售后</li>
			</ul>
			<div class="order-dian1">
				<div class="order-merchants">
					<img src="../../imgs/lufei.png" alt="">
					<p>小鱼的店 <i class="icon iconfont">></i></p>
					<span>等待卖家发货</span>
				</div>
				<div class="order-list">
					<dl class="order-show">
			            <dt><img src="../../imgs/food-show01.gif" alt=""></dt>
			            <dd>
			                <p class="order-show-title">维维嚼益嚼水果大豆棒橙味维维嚼益嚼水果大豆棒橙味...</p>
			                <p class="order-price">￥<span>109.00</span></p>
			                <p class="order-show-cheng">×1</p>	                    
			            </dd>
			        </dl>
			        <dl class="order-show">
			            <dt><img src="../../imgs/food-show02.gif" alt=""></dt>
			            <dd>
			                <p class="order-show-title">维维嚼益嚼水果大豆棒橙味维维嚼益嚼水果大豆棒橙味...</p>
			                <p class="order-price">￥<span>109.00</span></p>
			                <p class="order-show-cheng">×1</p>	                    
			            </dd>
			        </dl>

				</div>
				<div class="order-heji">
					<div class="heji-num">
						<p>合计：￥<span>114.00</span></p>
						<p>（运费：￥5.00）</p>
					</div>
					<div class="heji-btn">
						<button>提醒卖家发货</button>
						<button>申请退款</button>
					</div>
				</div>
			</div>
			
			<div class="order-dian2">
				<div class="order-merchants">
					<img src="../../imgs/lufei.png" alt="">
					<p>小鱼的店 <i class="icon iconfont">></i></p>
					<span>已发货</span>
				</div>
				<div class="order-list">
					<dl class="order-show">
			            <dt><img src="../../imgs/food-show01.gif" alt=""></dt>
			            <dd>
			                <p class="order-show-title">维维嚼益嚼水果大豆棒橙味维维嚼益嚼水果大豆棒橙味...</p>
			                <p class="order-price">￥<span>109.00</span></p>
			                <p class="order-show-cheng">×1</p>	                    
			            </dd>
			        </dl>
				</div>
				<div class="order-heji">
					<div class="heji-num">
						<p>合计：￥<span>114.00</span></p>
						<p>（运费：￥5.00）</p>
					</div>
					<div class="heji-btn">
						<button>查看物流</button>
						<button>申请退货</button>
						<button>确认收货</button>
					</div>
				</div>
			</div>
			<p class="order-di">到底了哦！</p>
		</main>
	</div>
</template>
<script>
	export default{

	}
</script>
<style>
	.order {
	 	width:100%;
	 	height:100%;
		background: #f6f6f6;
	  	display:flex;
	 	flex-direction: column;
	}

	.order .order-header {
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

	.order .order-header span i {
		width: 15%;
		text-align: center;
	}

	.order .order-header b {
		padding-left: 28px;
		font-size: 16px;
		font-weight: normal;
	}
	.order .order-header .order-header-mess{
		width: 15%;
		text-align: center;
	}
	.order-header .order-header-mess img{
		width: 22px;
		height: 20px;
		margin-top: 15px;
	}

	.order .order-main{
        -webkit-flex: 1;
        overflow-y: scroll;
        background: #f3f3f3;
    }
    .order-main .order-switch{
    	display: flex;
    	height: 50px;
    	line-height: 50px;
    	background: #fff;
    }
    .order-switch li{
    	flex: 1;
    	text-align: center;
    	font-size: 14px;
    	color: #666;
    	border-bottom: 1px solid #f2f2f2;
    }
    .order-switch .li1{
    	border-bottom: 2px solid red;
    }

    .order-dian1{
    	background: #fff;
    }

    .order-merchants{
    	display: flex;
    	padding-top: 5px;
    	padding-bottom: 5px;
    	padding-left: 12px;
    	border-bottom: 1px solid #f2f2f2;
    	position: relative;
    }
    .order-merchants img{
    	width: 40px;
    	height: 40px;
    }
	.order-merchants p{
		line-height: 40px;
		margin-left: 10px;
		font-size: 14px;
		color: #666;
	}
	.order-merchants span{
		line-height: 40px;
		font-size: 14px;
		color: tomato;
		position: absolute;
		right: 12px;
	}

    .order-list{
        background: #fff;
    }

    .order-list dl{
        /*margin-left: 10px;*/
        display: flex;
        height: 130px;
        border-bottom: 1px solid #f2f2f2;
        padding: 12px;
    }
    .order-list dt{
        width: 110px;
        height: auto;
        padding: 15px 5px;
        border: 1px solid #ccc;
    }
    .order-list dt img{
        width: 100%;
        height: 100%;
    }
    .order-list dd{
        flex: 1;
        margin-left: 10px;
        position: relative;   
    }
    dd .order-show-title{
        font-size: 14px;
        color: #666;
    }
    dd .order-price{
        position: absolute;
        bottom: 10px;
        color: red;
    }
    dd .order-price span{
        font-size: 18px;
    }
    .order-show-cheng{
    	position: absolute;
    	right: 0;
        bottom: 10px;
    	font-size: 16px;
    }

    .order-heji{
    	position: relative;
    	height: 95px;
    	border-bottom: 1px solid #f2f2f2;
    }
   	.order-heji .heji-num{
		position: absolute;
		right: 10px;
		top: 10px;
   		display: flex;
   	}
   	.order-heji .heji-num p{
   		font-size: 14px;
   		color: #888;
   	}
   	.order-heji .heji-num p span{
   		font-size: 18px;
   		color: #222;
   	}
   	.order-heji .heji-num p:nth-child(2){
   		font-size: 12px;
		margin-top: 6px;
   	}
   	.order-heji .heji-btn{
   		position: absolute;
		right: 10px;
		bottom: 15px;
   		margin-top: 10px;
   	}
   	.order-heji .heji-btn button{
   		padding: 5px 15px;
   		font-size: 14px;
   		background: #fff;
   		color: #666;
   		border: 1px solid #888;
   		border-radius: 5px;
   		margin-right: 10px;
   	}
   	.order-heji .heji-btn button:last-child{
   		margin-right: 0;
   	}

   	.order-dian2{
   		background: #fff;
   		margin-top: 10px;
   	}


   	.order-di{
   		height: 50px;
   		line-height: 50px;
   		text-align: center;
   		color: #666;
   	}
</style>