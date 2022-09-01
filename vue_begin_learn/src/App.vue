<script>
	export default{
		data(){
			return{
				num:0,
				uname:"秦文杰",
				msg:"<h2>这是html标签内容</h2>",
				pic:"https://www.baidu.com/img/flexible/logo/pc/result@2.png",
				id:'p1',
				element_name:'id',
				mouse_event:'click',
			}
		},
		methods:{
			change_num:function(){
				this.num ++;
			},
			change_color:function(){
				if (this.id=='p1'){
					this.id = 'p2';
				}
				else{
					this.id = 'p1';
				}
			},
		}
	};
</script>

<template>
  <div>
    <p>{{num}}</p>
	<P>{{uname}}</P>
	<!-- 定义它的元素或组件只渲染一次，包括元素或 组件的所有子节点。首次渲染后，不再随数据的变化重新渲染，将被视为静态内容 -->
	<P v-once>{{num}}</P>
	<p><button @click="change_num">改变num</button></p>
	<!-- v-htmlmsghtml标签解析后输出,避免使用，否则会带来危险(XSS攻击 跨站脚本攻击),永不用在用户提交的内容上; -->
	<P v-html="msg"></P>
	<!-- v-bind 动态绑定属性内容 -->
	<img v-bind:src="pic" alt="">
	<p :id="id">动态绑定id样式</p>
	<p><button @click="change_color">红蓝配</button></p>
	<!-- 直接使用js表达式 -->
	<p id="p2">{{uname.split('').reverse().join('')}}</p>
	<!-- v-on 监听DOM事件  语法糖为@ -->
	<p><button v-on:click="change_color">红蓝配</button></p>
	<!-- 动态参数,动态属性 -->
	<p v-bind:[element_name]='id'>动态属性绑定</p>
	<p><button @click="element_name='class'">改变属性</button></p>
	<!-- 动态事件 -->
	<p><button @[mouse_event]="element_name='class'">动态事件</button></p>
	<p><button @click="mouse_event='mouseover'">改变事件</button></p>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
#p1{
	color: #646cffaa;
}
#p2{
	color: brown;
}
.p1{
	font-size: 50px;
}
</style>
