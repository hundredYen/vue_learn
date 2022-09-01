<script>
	export default{
		data(){
			return{
				message:"你好",	
				istest:true,
				error:null,
				class_list:['test','bg'],
			}
		},
		computed:{
			classObj:function(){
				return{
					test:this.istest && !this.error,
					bg:!this.error ,
					
				}
			}
		}

	};
</script>

<template>
  <div>
   <!-- 直接绑定样式-->
   <p class="test">芜湖</p>
   <!--放置对象 -->
   <p :class="{test:istest}" >起飞</p>
   <button @click="istest=false" >改变istest</button>
   <!-- 使用计算器放置对象-->
   <p :class="classObj">铸币吧</p>
   <!-- 数组语法 不常用-->
   <p :class="class_list">傻逼公司</p>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #2affcaaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.test{
	color: aqua;
	font-size: 50px;
}
.bg{
	background-color: #2affcaaa;
}

</style>
