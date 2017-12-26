
<template>
	<span>
		<span v-for="item in rollerNumber">{{item}}</span>
	</span>
</template>

<script>
	export default {
		name:'epRoller',
		data(){
			return {
				rollerNumber:[],
				timer:null,
				timer2:null
			}
		},
		props:{
			number:{
				default:'0'
			},
			rate:{	//一次赋值动作中，各单位数值滚动频率
				type:Number,
				default:100
			},
			duration:{	//一次赋值动作滚动时间
				type:Number,
				default:500
			}
		},
		watch:{
			number(newVal){
				this.handleNumber(newVal);
			}
		},
		methods: {
			handleNumber(newVal){
				
				if(typeof(newVal) === "number"){	//防止后端接口给的数值是number类型:newVal.length会报错
					newVal = newVal+'';
				}
				
				clearTimeout(this.timer2);	//清除延迟定时器(不清除，短时间也没事，按标准来吧)
				
				let _this = this;	//解决匿名函数不能正确访问this
				
				this.timer = setInterval(function(){
					
					_this.rollerNumber = [];	//每刷新一次，则清空，不然会叠加
					
					for(let i =0;i<newVal.length;i++){
						_this.rollerNumber.push(parseInt(Math.random()*(9+1),10));	//0~9的随机数：parseInt(Math.random()*(9+1),10)
					}
					
				},this.rate);
				
				this.timer2 = setTimeout(function(){
					
					clearInterval(_this.timer);	//关闭定时器
					_this.rollerNumber = newVal.split('');	//随机完，设置正确的值
				},this.duration);
			}
		},
		mounted: function () {
			
			this.$nextTick(function () {	//保险写法
		  		this.handleNumber(this.number);	
			})
		}
	}
</script>

<style>
	
</style>