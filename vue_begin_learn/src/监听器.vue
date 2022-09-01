<script>
	export default{
		data(){
			return{
				message:"你好",
				age:0,
				user:{
					name:'qwj',
				},
				
			}
		},
		/* 计算属性computed * 依赖值不变，不会重新计算，达到缓存的效果 */
		computed:{
			reverse_msg:function(){
				return this.message.split('').reverse().join('');
			}
		},
		/* 计算属性完整写法 每一个计算属性中都有一个getter 和 setter */
		// computed:{
		// 	reverse_msg:{
		// 		set:function(){ //设置或者更改计算属性调用
					
		// 		},
		// 		get:function(){
		// 			return this.message.split('').reverse().join('');
		// 		},
				
		// 	},
		// },
		methods:{
			
		},
		watch:{ //监听数据的变化，执行异步操作(计算属性做不到)，或者复杂逻辑代码
			/* 每当message发生变化，调用函数 */
			// message:function(newValue,oldValue){
			// 	console.log(newValue);
			// 	console.log(oldValue);
			// },
			message:{
				immediate:true, //true 表示初始化就调用
				handler:function(newMessage){
					if(newMessage.length<5 || newMessage.length>11){
						console.log("请重新输入");
					}
				},
			},
			/* watch 监听不到对象属性变化，要使用深度监听 */
			// user:function(newValue){
			// 	console.log(newValue);
			// },
			// user:{
			// 	handler:function(newValue){
			// 		console.log(newValue);
			// 	},
			// 	deep:true  //开启深度监听 监听器会一层层遍历 给每个对象深度监听
			// }
			"user.name":{ //使用字符串形式进行监听
				handler:function(newValue){
					console.log(newValue);
				},
				
			}
		},
	};
</script>

<template>
  <div>
    <p>{{message}}</p>
	<p>{{reverse_msg}}</p>
	<button @click="message='起飞了'">改变message</button>
	<!-- v-model 数据双向绑定 -->
	<input type="text" v-model="message"/>
	<p>{{user.name}}</p>
	<button @click="user.name='芜湖'">改变用户名字</button>
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

</style>
