<template>
	<div class="address">
		<header class="address-header">
			<router-link :to="{name:'site'}"><i class="iconfont icon-back"></i></router-link>
			<b>收货地址</b>
			<i class="iconfont icon-home"></i>
		</header>

		<main class="address-main">

			<div class="per-name">
				<input type="text" placeholder="收货人姓名" v-model="name">
			</div>

			<div class="per-phone">
				<input type="text" placeholder="手机号" v-model="phone">
			</div>

			<div class="per-provinces">
				<select name="provinces" v-model="city">
					<option value="0" selected="selected">请选择省份</option>
					<option :value="x.name" v-for="x in city_list">{{x.name}}</option>
				</select>
				<select name="city" v-model="pro">
					<option value="0" selected="selected">请选择城市</option>
					<option :value="x" v-for="x in pro_list">{{x.name}}</option>
				</select>
			</div>

			<div class="per-area">
				<select name="area" v-model="area">
					<option value="1">请选择地区</option>
					<option value="1" v-for="x in area_list">{{x}}</option>
				</select>
			</div>

			<div class="per-address">
				<input type="text" placeholder="详细地址" v-model="site">
			</div>

			<div class="set-default">			
				<i class="btns icon iconfont" :class="{'icon-check':selected}" @click="select_fn"></i>
				<span>设为默认地址</span>
			</div>

			<div class="address-btn">
				<button @click="save">保存</button>
			</div>
		</main>
	</div>
</template>
<script>
	export default {
	    data() {
	        return {
	            selected: false,
	            name: "",
	            phone: "",
	            site: "",
	            title: "",
	            Show: false,
	            city: "",
	            city_list: [], 
	            pro: "",
	            pro_list: [],
	            area_list: [],
	            area: ""
	        }
	    },
	    watch:{
	        city:function(newv){
	            this.city_list.forEach((v,i)=>{                   
	                if(v.name == newv){
	                    this.pro_list = v.city;	                    
	                }
	            })  
	        },
	        pro:function(newy){	            
	           	this.pro_list.forEach((v,i)=>{
	            	if(v.name == newy.name){
	                    this.area_list = v.area;
	                }
	            })
	            //console.log(this.area_list)
	        }
	    },
	    created(){
	        this.$http.post("/h5/mtop").then((res)=>{	            
	            this.city_list =  res.data;               
	        })
	    },
	    methods: {
	        select_fn(idx) {
	            this.selected = !this.selected;
	        },
	        save(){
	            let reg_phone=/^1[34578]\d{9}$/;
	            let str = "";
	            if(!this.name){
	              str = " 请输入姓名";
	             this.dialog()
	            }else if(!this.phone){
	               str = "手机号不能为空";
	             this.dialog()
	            }
	            else if(!reg_phone.test(this.phone)){
	                str="手机号错误，请重新输入";
	                this.dialog()
	            }else{
	                this.$router.push("/site")
	            }
	            this.title = str;
	        },
	        dialog(){
	            this.Show = true;
	            setTimeout(() => {
	                this.Show = false;
	                
	            },1500)
	        }
	    }
	}
</script>
<style>
	.address {
	 	width:100%;
	 	height:100%;
	  	display:flex;
	 	flex-direction: column;
	 	box-sizing: border-box;
	}

	.address-header {
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
	.address-header b{
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
	

	.address .address-main{
	    -webkit-flex: 1;
	    overflow-y: scroll;
	    background: #f5f5f5;
	    padding: 0 15px;
	    font-size: 14px;
	}
	.per-name, .per-phone, .per-provinces, .per-area, .per-address{
		margin-top: 15px;
	}
	.per-name input, .per-phone input, .per-address input{
		width: 100%;
		line-height: 40px;
		border: none;
		border-radius: 3px;
		padding-left: 10px;
	}
	.per-provinces, .per-area{
		display: flex;
		justify-content: space-between;
	}
	.per-provinces select, .per-area select{
		border: none;
		border-radius: 3px;
		height: 40px;
		line-height: 40px;
		width: 40%;
		padding-left: 10px;
		/*font-weight: normal;
	    display: block;
	    white-space: pre;
	    min-height: 1.2em;*/
	}
	.per-area select{
		width: 100%;
	}
	option{
	}

	.address-main .set-default{
		position: relative;
		margin-top: 15px;
	}
	.address-main .set-default .btns{
		width: 25px;
		height: 25px;
		font-size: 14px;
		border:  1px solid #ccc;
		border-radius: 50%;
		overflow: hidden;
		text-align: center;
		color: #fff;
		position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        margin: auto;
	}
	.address-main .set-default span{
		margin-left: 35px;
		color: #666;
	}
	.icon-check {
		background: #fc4141;
	}

	.address-btn{
		width: 100%;
		margin-top: 30px;
		position: relative;
	}
	.address-btn button{ 
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
		/*box-shadow: 2px 2px 0px 1px #ccc;*/
	}
</style>