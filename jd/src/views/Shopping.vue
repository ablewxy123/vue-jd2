<template>
	<div id="shopping-cart">
		<div>爱好：{{hobby}}</div>
		<label><input type="checkbox" v-model="hobby" value="钓鱼">钓鱼</label>
		<label><input type="checkbox" v-model="hobby" value="跑步">跑步</label>
		<label><input type="checkbox" v-model="hobby" value="看电影">看电影</label>
		<label><input type="checkbox" v-model="hobby" value="听音乐">听音乐</label>
		<label><input type="checkbox" v-model="hobby" value="看书">看书</label>
		<label><input type="checkbox" v-model="hobby" value="打游戏">打游戏</label>
		<div>
			<div>{{agree}}</div>
			<label>
				<input type="checkbox" v-model="agree" >
			</label>
		</div>
	</div>
</template>

<script>
	import TabBar from "@/components/TabBar.vue";
	export default{
		data(){
			return{
				hobby:[],
				agree:true,

			}
		}
	}
</script>

<style>
</style>