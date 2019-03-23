<template>
	<div class="sku mask" v-show="value" @click="close">
		<transition name="slide">
			<div class="main" v-show="value" @click.stop>
				<div class="header">
					<img src="//m.360buyimg.com/mobilecms/s750x750_jfs/t1/18026/21/4530/159447/5c32bd70E2ba4e125/7cea8f457f694083.jpg!q80.dpg.webp"/>
					<p class="price">¥<em>99.00</em></p>
					<p class="prop"></p>
					<p class="selected"><span>已选：{{choose[navIndex].title}},{{size[navIndex2].num}},{{inputVal}}件</span></p>
				</div>
				<div class="body">
					<div class="popupSkuArea">
						<div class="sku_kind">颜色</div>
						<div class="sku_choose" >
							<span class="item" v-for="(item,index) in choose" v-text="item.title" :key="index"  @click="navIndex=index" :class="{active:navIndex==index}"></span>
						</div>
						<div class="sku_kind">尺码</div>
						<div class="sku_choose">
							<span class="item" lass="item" v-for="(item,index) in size" v-text="item.num" :key="index"  @click="navIndex2=index" :class="{active:navIndex2==index}"></span>
						</div>
						<div class="count_choose">
							<div class="num_wrap_v2 flex">
								<span class="minus" @click="inputVal>1?inputVal--:1"><i class="row"></i></span>
								<div class="text_wrap flex-item">
									<input type="text" name="" id="" value="" v-model="inputVal"/>
								</div>
								<span class="plus" @click="inputVal++"><i class="row"></i><i class="col"></i></span>
							</div>
							<p class="count">数量</p>
							
						</div>
						
					</div>
				</div>
				<div class="btn" @click="ok">
					确定
				</div>
			</div>
		</transition>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				navIndex:0,
				navIndex2:0,
				inputVal:1,
				// show: true
				choose:[{
					title:'灰色-加棉款'
				},{
					title:'灰色-四季款'
				},{
					title:'蓝色-四季款'
				},{
					title:'黑色-四季款'
				},{
					title:'灰色-透气款'
				},{
					title:'灰色-加棉款'
				},{
					title:'灰色-加棉款'
				}, ],
				size:[{
					num:'#38'},{
					num:'#39'},{
					num:'#40'},{
					num:'#41'},{
					num:'#42'},{
					num:'#43'},{
					num:'#44'},{
					num:'#45'}]
				
			};
		},
		props: {
			value: {
				type: Boolean,
				default: false
			}
		},
		methods:{
			close(){
				this.$emit('input', false);
			},
			ok() {
				this.$emit('ok', this.choose[this.navIndex],this.size[this.navIndex2],this.inputVal);
			}
		}
	}
</script>

<style>
	.mask {
		position: fixed;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		background-color: rgba(0, 0, 0, .7);
		z-index: 999999;
	}
	
	.mask .main {
		width: 100%;
		height: 9.2rem;
		background-color: #FFFFFF;
		position: absolute;
		bottom: 0;
		left: 0;
	}
	
	.sku .slide-enter {
		bottom: -9.2rem;
	}
	
	.sku .slide-enter-active {
		transition: bottom 0.3s;
	}
	
	.sku .slide-enter-to {
		bottom: 0;
	}
	
	.sku .slide-leave {}
	
	.sku .slide-leave-active {}
	
	.sku .slide-leave-to {}
	.header {
		padding: 0 0 0.2rem 2.2rem;
		height: 1.4rem;
		line-height: 0.92rem;
		background-color: #fff;
		position: relative;
	    font-size: 0.32rem;
	    color: #333;
	    background-color: #f7f7f7;
	}
	
	.header img{
		position: absolute;
	    left: 0.2rem;
	    top: -0.4rem;
	    border-radius: 0.04rem;
	    width: 1.8rem;
	    height: 1.8rem;
	}
	.header .price {
		margin: 0;
		display: inline-block;
		height: 0.8rem;
		line-height: 0.8rem;
		color: #e4393c;
		font-size: 0.2rem;
		width: 100%;
		text-align: left;	}
	.header .selected {
		word-break: break-all;
		font-size: 0.24rem;
		color: #333;
		line-height: 1.4em;
		padding-right: 0.2rem;
		text-align: left;
	}
	.sku .header .selected span {
		color: #999;
	}
	.header .porp{
		word-break: break-all;
	    font-size: 0.24rem;
	    color: #333;
	    line-height: 1.4em;
	    padding-right: 0.2rem;
	}
	.body{
		    box-sizing: border-box;
	    max-height:7.58rem;
	    padding-bottom: 2rem;
	        overflow: auto;
	}
	.sku_kind{
		    font-size: 0.24rem;
		    color: #999;
		    margin: 0 0.2rem;
		    height: 0.8rem;
		    line-height: 0.8rem;
		    text-align: left;
	}
	.sku_choose{
		    overflow: hidden;
    		margin-bottom:0.06rem;
	}
	.sku_choose .item{
		display: inline-block;
	    padding: 0 0.2rem;
	    min-width: 0.4rem;
	    max-width: 5.4rem;
	    overflow: hidden;
	    height: 0.6rem;
	    line-height: 0.6rem;
	    float: left;
	    text-align: center;
	    margin-left: 0.2rem;
	    margin-bottom: 0.2rem;
	    border-radius: 0.2rem;
	    color: #333;
	    background-color: #f7f7f7;
	    font-size: 0.28rem;
	}
	.sku_choose .active{
		background-color: #e4393c;
    	color: #fff;
	}
	.count_choose{
		 padding: 0 0.2rem 0.26rem;
    	font-size: 0.24rem;
	}
	.count_choose .num_wrap_v2{
		position: relative;
	    z-index: 0;
	    width: 2.2rem;
	    float: right;
	    vertical-align: middle;
	    height: 0.6rem;
	}
	.count_choose .num_wrap_v2 .minus{
		border-top-left-radius: 0.06rem;
    	border-bottom-left-radius: 0.06rem;
	}
	.count_choose .num_wrap_v2 span{
		    position: relative;
		    max-width: 0.6rem;
		    min-width: 0.6rem;
		    height: 0.6rem;
		    line-height: 0.6rem;
		    background: #f7f7f7;
		    text-align: center;
		    display: inline-block;
	}
	.num_wrap_v2 span .row{
		    border-radius: 0.4rem;
		    position: absolute;
		    top: 50%;
		    left: 50%;
		    margin-left: -0.14rem;
		    margin-top: -0.02rem;
		    width: 0.28rem;
		    height: 0.04rem;
		    background-color: #999;
	}
	.num_wrap_v2 .text_wrap{
		    position: relative;
	    width: 0.9rem;
	    z-index: 0;
	    margin: 0 0.02rem;
	    display: inline-block;
	}
	.num_wrap_v2 .text_wrap input{
		background: #f7f7f7;
		 height: 0.6rem;
	    width: 100%;
	    color: #333;
	    background: #fff;
	    font-size: 0.24rem;
	    text-align: center;
	    border: none;
	    outline: none;
	}
	 .num_wrap_v2 .plus {
    border-top-right-radius: 0.06rem;
    border-bottom-right-radius: 0.06rem;
}
.num_wrap_v2 span .col {
    border-radius: 0.4rem;
    position: absolute;
    top: 50%;
    left: 50%;
    margin-left: -0.02rem;
    margin-top: -0.14rem;
    width: 0.04rem;
    height: 0.28rem;
    background-color: #999;
}
 .count_choose .count{
 	    color: #999;
    height: 31px;
    line-height: 31px;
    text-align: left;
 }
 .service_choose{
 	position: relative;
    padding: 0 10px;
    color: #999;
    font-size: 0.28rem;
    text-align: left;
    margin: 0;
 }
 .service_choose .title {
    font-size: 0.24rem;
    height: 0.8rem;
    line-height: 0.8rem;
    margin: 0;
}
.service_choose .service .name{
	
    position: relative;
    padding: 0 0 0.2rem 0.5rem;
    font-size: 0.28rem;
    color: #333;
    font-weight: 400;
    margin: 0;
}
.sku .btn{
	width: 100%;
	height: 1rem;
	line-height: 1rem;
	position: absolute;
	left: 0;
	bottom: 0;
	font-size: 0.32rem;
	background-color: #e4393c;
}
</style>