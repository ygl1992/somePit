# js中'0'到底是true还是false

	if( '0' ){
		alert("'0' is true");
	}
	
	if( '0' == false ){
		alert("'0' is false");
	}

结果是，两次都alert了！那么'0'到底是true还是false呢？

其实js做比较的时候，有这样三条规则：

- 如果比较的两者中有boolean，会把boolean先转换为对应的number，即0和1（false是0，1是true）

- 如果比较的双方有一方为number，一方为string，会把string转换为数字
 
- 把string直接转换为boolean的时候，空字符串''转换为false，除此之外的一切字符转换为true