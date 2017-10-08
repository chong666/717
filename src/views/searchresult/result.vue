<template>
  <div class="search_box">
      <header class="heade">
      	<span class="iconfont icon-back"></span>
      	<span>
      		<input type="text">
      	</span>
      </header>
      <section class="main">
      	<div class="banner">
      		<!-- <div class="banner_img"></div> -->
      		<div class="banner_img">
      			<img src="../../imgs/未标题-7.png" alt="">
      		</div>
      		<div class="banner_txt">
      			抱歉，没有找到符合要求的商品
      		</div>
      	</div>
      </section>
  </div>
</template>
<script>
	export default{
		
	}
	
</script>
<style scoped>
	.search_box{
		width: 100%;
		height: 100%;
		background: #eee
	}
	.search_box .heade{
		width: 100%;
		height: 0.88rem;
		line-height: 0.88rem;
		
		border-bottom: 1px solid #ccc;
		padding: 0 8px;
		background: #fff;
		font-size: 0.22rem;

	}
	.heade span:nth-child(1){
		padding-right:10px;
	}
	.heade span:nth-child(2) input{
		width:80%;
		height:25px;
		border-radius: 10px;
		border:none;
		background: #eee;
		outline: none;
	}
	.main{
		width: 100%;
	  	flex:1;
		overflow: hidden;
		overflow-y: scroll;
	}
	.banner{
		background: #fff;
		text-align: center;
	}
	.banner{
		height:250px;
	}
	.banner_img{
		height:150px;
		line-height: 150px;
		position: relative;
	}
	.banner_img img{
		width: 80px;
		height: 80px;
		border:1px solid #ccc;
		position: absolute;
		bottom: 10px;
		left: 0;
		right:0;
		margin: auto;
		border-radius: 50%;
		
	}
	.banner_txt{
		margin-top: 10px;
	}
</style>
