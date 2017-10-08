<template>
	<div class="balance">
		<header class="balance-header">
			<div class="bal-top">				
				<router-link :to="{name:'mine'}"><i class="iconfont icon-back"></i></router-link>
				<b>账户余额</b>
				<span>明细</span>
			</div>
			<div class="bal-bottom">
				<p>账户余额</p>
				<b>0.00</b>			
			</div>
		</header>
		<main class="balance-main">
			<ul>
				<li>
					<img src="../../imgs/yue.gif" alt="">
					<p>充值</p>
					<b class="icon iconfont icon-more">></b>
				</li>
				<li>
					<img src="../../imgs/tixian.gif" alt="">
					<p>提现</p>
					<b class="icon iconfont icon-more">></b>
				</li>
			</ul>
		</main>
	</div>
</template>

<script>

</script>

<style>
	.balance{
	
	}

	.balance-header{
		background: #469efc;
		color: #e0f1ff;
		padding: 0 10px;
		border-bottom: 1px solid #4199fc;
	}
	.balance-header .bal-top{
		height: .88rem;
		line-height: .88rem;
		display: flex;
		justify-content: space-between;
		flex-shrink: 0;
	}
	.balance-header .bal-top .iconfont{
		color: #fff;
	}
	.balance-header .bal-top b{
		font-size: 18px;
		color: #fff;	
	}
	
	.balance-header .bal-bottom{
		padding-bottom: 20px;
	}
	.balance-header .bal-bottom p{
		margin-top: 30px;
		font-size: 16px;
	}
	.balance-header .bal-bottom b{
		margin-top: 10px;
		font-size: 50px;
		color: #fff;
	}

	.balance-main{

	}
	.balance-main ul{
		
	}
	.balance-main ul li{
		padding: 10px 0;
		border-bottom: 1px solid #e5e5e5;
		display: flex;
		position: relative;
	}
	.balance-main ul li img{
		width: 30px;
		height: 30px;
		margin-left: 10px;
	}
	.balance-main ul li p{
		line-height: 30px;
		font-size: 14px;
		color: #666;
		margin-left: 10px;
	}
	.balance-main ul li .iconfont{
		position: absolute;
		right: 10px;
		line-height: 30px;
		color: #666;
	}	
</style>