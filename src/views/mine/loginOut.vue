<template>
	<div class="loginOut">
		<header class="loginOut-header">
			<router-link :to="{name:'mine'}"><i class="iconfont icon-back"></i></router-link>
			<b>设置</b>
			<i class="iconfont icon-home" @click="go_to_settings"></i>
		</header>
		<main class="loginOut-main">
			<ul class="loginOut-mess">				
				<li class="my-head">
					<div class="wode">
						<p>我的头像</p>
						<img src="../../imgs/未标题-7.png" alt="">						
					</div>
					<b class="iconfont icon-more">></b>
				</li>
				<li class="user-name">
					<div class="wode">
						<p>用户名</p>					
						<span>路飞</span>
					</div>
					<b class="iconfont icon-more">></b>
				</li>
				<li class="my-code">
					<div class="wode">
						<p>我的二维码名片</p>						
						<img src="../../imgs/erweima.png" alt="">
					</div>
					<b class="iconfont icon-more">></b>
				</li>
				<li class="my-phone">
					<div class="wode">						
						<p>绑定手机号</p>
					</div>
					<b class="iconfont icon-more">></b>
				</li>
			</ul>
			<div class="loginOut-btn">
				<button>退出登录</button>
			</div>
		</main>
	</div>
</template>
<script>	
	export default {
        methods:{
            go_to_settings(){
                this.$router.push("/settings")
            }
        }
    }
</script>
<style>
	.loginOut{
		width:100%;
	 	height:100%;
	  	display:flex;
	 	flex-direction: column;
	 	box-sizing: border-box;
	}

	.loginOut-header{
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
	.loginOut-header b{
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

    .loginOut-main{
	    -webkit-flex: 1;
	    overflow-y: scroll;
	    background: #f5f5f5;
	    font-size: 14px;
	}
	.loginOut-main .loginOut-mess{
		background: #fff;
		margin-top: 8px;
	    padding: 0 15px;
	}
	.loginOut-mess li{
		/*display: flex;*/
		padding: 10px 0;
		border-bottom: 1px solid #eee;
		position: relative;
	}
	.loginOut-mess li .wode{
		width: 95%;
		display: flex;		
		justify-content: space-between;
	}
	.loginOut-mess .my-head p{
		margin-top: 20px;
	}
	.loginOut-mess .my-head img{
		width: 54px;
		height: 54px;
	}

	.loginOut-mess .my-code p{
		margin-top: 12px;
	}
	.loginOut-mess .my-code img{
		width: 40px;
		height: 40px;
	}

	.loginOut-mess .iconfont{
		position: absolute;
		right: 0;
		bottom: 8px;
		color: #999;
	}
	.my-head .iconfont, .my-code .iconfont{
		margin-bottom: 10px;
	}

	.loginOut-btn{
		margin-top: 50px;
		position: relative;
	}
	.loginOut-btn button{
		position: absolute;
		left: 0;
		right: 0;
		width: 70%;
		margin: 0 auto;
		height: 45px;
		line-height: 45px;
		background: #fc4141;
		color: #fff;
		border: none;
		border-radius: 30px;
		font-size: .28rem;
	}
</style>