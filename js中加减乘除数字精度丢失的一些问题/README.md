# js中加减乘除数字精度丢失的一些问题

### 原因
计算机的二进制实现和位数限制有些数无法有限表示。JS遵循IEEE754规范，采用双精度存储，占用64bit

### 例子
0.1+0.2  >> 0.30000000000000004

0.3-0.1  >> 0.19999999999999998

4246.77*100 >> 424677.00000000006

### 解决方案
// 保留一位小数	<br />
((number) * 10).toFixed(0) / 10

// 保留两位小数	<br />
((number) * 100).toFixed(0) / 100

// 保留三位小数	<br />
((number) * 1000).toFixed(0) / 1000


### 注意
toFixed四舍五入并不是真正的四舍五入
1.35.toFixed(1) // 1.4 正确	<br />
1.335.toFixed(2) // 1.33  错误 <br />
1.3335.toFixed(3) // 1.333 错误	<br />
1.33335.toFixed(4) // 1.3334 正确 <br />
1.333335.toFixed(5)  // 1.33333 错误	<br />
1.3333335.toFixed(6) // 1.333333 错误 <br />
IE浏览器下这些都是正确的


### 第三方插件库
[mathjs](https://github.com/josdejong/mathjs)

1.2 / (3.3 + 1.7) <br />
	<span style="color:#c00; margin-left:30px">0.24</span> <br />
a = 5.08 cm + 2 inch <br />
	<span style="color:#c00; margin-left:30px">10.16 cm</span> <br />
a to inch <br />
	<span style="color:#c00; margin-left:30px">4 inch </span> <br />
sin(90 deg) <br />
	<span style="color:#c00; margin-left:30px">1 </span> <br />
f(x, y) = x ^ y <br />
	<span style="color:#c00; margin-left:30px">f(x, y) </span> <br />
f(2, 3) <br />
	<span style="color:#c00; margin-left:30px">8 <br /></span>
