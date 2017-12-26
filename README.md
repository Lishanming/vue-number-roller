# vue-number-roller
A vue component provide rolling effect when the specified number change

使用场景：
一些大屏显示的页面中，当数字发生改变时，需要表现类似摇奖机一样的滚筒效果

![image](https://github.com/Lishanming/vue-number-roller/blob/master/example.gif?raw=true)

### How to use?

```
npm install vue-number-roller --save
```

```
import roller from 'vue-number-roller'
Vue.use(roller)
```

```
<ep-roller :number = "rollNumber" :rate="100" :duration="500"></ep-roller>
```
### property

属性 | 描述 | 默认值（ms）
---|--- |---
number | 显示数值 | 
rate   | 一次赋值动作中，各单位数值滚动频率 一次赋值动作滚动时间 | 100
duration | 一次赋值动作滚动时间 | 500

