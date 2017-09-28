# jQuery-JavaScript一览表

## CSS选择器
### 元素选择
	// jQuery
	$("li").css("color", "red");

	// JavaScript
	document.querySelectorAll('li').forEach(el => {
	  	el.style.color = 'red';
	});

### ID选择
	// jQuery
	$('li#first').css('color', 'red');

	// JavaScript
	document.querySelector('li#first').style.color = 'red';

### 类选择
	// jQuery
	$('li.first').css('color', 'red');

	// JavaScript
	document.querySelectorAll('li.first').foreach(el => {
	  	el.style.color = 'red';
	});

### 子元素选择
	// jQuery
	$('.first strong').css('color', 'red');

	// JavaScript
	document.querySelectorAll('.first strong').forEach(el => {
	  	el.style.color = 'red';
	});

### 通配符选择
	// jQuery
	$('li *').css('color', 'red');

	// JavaScript
	document.querySelectorAll('li *').forEach(el => {
	  	el.style.color = 'red';
	});

### 分组选择
	// jQuery
	$('#first, #third').css('color', 'red');

	// JavaScript
	document.querySelectorAll('#first, #third').forEach(el => {
	  	el.style.color = 'red';
	});

### 伪类选择
	// jQuery
	$('li:first-child').css('color', 'red');

	// JavaScript
	document.querySelectorAll('li:first-child').forEach(el => {
	  	el.style.color = 'red';
	});

### 匹配选择
	// jQuery
	$('#second ~ li').css('color', 'red');

	// JavaScript
	document.querySelectorAll('#second ~ li').forEach(el => {
	  	el.style.color = 'red';
	});

### 属性选择
	// jQuery
	$('[class="first"]').css('color', 'red');
	// [attribute!="..."]                 -> 选择指定属性不等于这个值的元素
	// [attribute^="..."]                 -> 选择指定属性是以给定字符串开始的元素
	// [attribute$="..."]                 -> 选择指定属性是以给定字符串结尾的元素
	// [attribute*="..."]                 -> 选择指定属性具有包含给定字符串的元素
	// [attribute="..."][attribute="..."] -> 设置多个指定属性
	
	// JavaScript
	document.querySelectorAll('[class="first"]').forEach(el => {
	  	el.style.color = 'red';
	});

### jQuery自带选择
	// jQuery
	$('li:first, li:last').css('color', 'red');
	$('li:even, li:odd').css('color', 'red');
	$('li:lt(2)').css('color', 'red');
	$('li:eq(2)').css('color', 'red');
	$('li:gt(2)').css('color', 'red');
	$(':header').css('color', 'red');
	$('li:contains("テキスト")').css('color', 'red');
	$('li:has(strong)').css('color', 'red');
	$('li:parent').css('color', 'red');
	
## HTML/CSS操作
### 修改文本	
	<p id="first">修改前</p>
	
	// jQuery
	$('p#first').text('Hello Rizu');

	// JavaScript
	document.querySelector('#first').textContent = 'Hello Rizu'

### 获取文本 
	<p id="first">获取的字符串</p>
	<p id="second">修改前</p>

	// jQuery
	$('p#second').text($('p#first').text());

	// JavaScript
	var text = document.querySelector('#first').textContent;
	document.querySelector('#second').textContent = text;

### 修改html		
	<p id="first">修改前</p>
	
	// jQuery
	$('p#first').html('<strong>Hello Rizu</strong>');

	// JavaScript
	document.querySelector('#first').innerHTML = '<strong>Hello Rizu</strong>';

### 获取html
	<p id="first"><strong>获取的HTML</strong></p>
	<p id="second">变更前</p>
	
	// jQuery
	$('p#second').html($('p#first').html());

	// JavaScript
	var html = document.querySelector('#first').innerHTML;
	document.querySelector('#second').innerHTML = html;

### 向html元素中的头部、尾部插入
	<p id="first">Hello Rizu</p>
	
	// jQuery
	$('p#first').prepend('<strong>在头部插入</strong>');
	$('p#first').append('<strong>在尾部插入</strong>');

	// JavaScript
	var target    = document.querySelector('#first');
	var a         = document.createElement('strong');
	a.textContent = '在头部插入';
	var b         = document.createElement('strong');
	b.textContent = '在尾部插入';
	target.insertBefore(a, target.firstChild);
	target.appendChild(b);

### 在html元素的前、后插入
	<p id="first">Hello Rizu</p>
	
	// jQuery
	$('p#first').before('<h1>前面插入</h1>');
	$('p#first').after('<h1>后面插入</h1>');

	// JavaScript
	var before         = document.createElement('h1');
	var after          = document.createElement('h1');
	before.textContent = '前面插入';
	after.textContent  = '后面插入';
	var target         = document.querySelector('#first');
	var parent         = target.parentNode;
	parent.insertBefore(before, target);
	parent.appendChild(after);
	
### 向html元素内的头部、尾部移动
	<p id="first">Hello Rizu</p>
	<strong id="prepend">向头部移动</strong>
	<strong id="append">向尾部移动</strong>
	
	// jQuery
	$('strong#prepend').prependTo('p');
	$('strong#append').appendTo('p');

	// JavaScript
	var prepend = document.querySelector('#prepend');
	var append  = document.querySelector('#append');
	var target  = document.querySelector('#first');
	target.insertBefore(prepend, target.firstChild);
	target.appendChild(append);
	
### 在html元素的前、后移动
	<strong id="after">向后移动</strong>
	<p id="first">Hello Rizu</p>
	<strong id="before">向前移动</strong>
	
	// jQuery
	$('strong#before').insertBefore('p');
	$('strong#after').insertAfter('p');

	// JavaScript
	var before = document.querySelector('#before');
	var after  = document.querySelector('#after');
	var target = document.querySelector('#first');
	var parent = target.parentNode;
	parent.insertBefore(before, target);
	parent.appendChild(after);

### 使用指定元素包裹各元素
	<p id="first">Hello Rizu</p>
	<p id="second">Hello yrq</p>
	
	// jQuery
	$('p').wrap('<h1></h1>');

	// JavaScript
	var target = document.querySelector('#first');
	var parent = target.parentNode;
	document.querySelectorAll('p').forEach((value, index) => {
	  	var wrap       = document.createElement('h1');
	  	wrap.innerHTML = value.outerHTML;
	  	if (index === 0) { parent.innerHTML = '';}
	  	parent.appendChild(wrap);
	});

### 将所有元素包裹在一个元素中
	<div>
	  	<p id="first">Hello Rizu</p>
	  	<p id="second">Hello yrq</p>
	</div>
	
	// jQuery
	$('p').wrapAll('<h1></h1>');

	// JavaScript
	var target       = document.querySelector('div');
	var p            = target.innerHTML;
	var h1           = document.createElement('h1');
	h1.innerHTML     = p;
	target.innerHTML = '';
	target.innerHTML = h1.outerHTML;

### 使用指定元素包裹各元素的子元素
	<div>
	  	<p id="first">Hello Rizu</p>
	  	<p id="second">Hello yrq</p>
	</div>
	
	// jQuery
	$('p').wrapInner('<strong></strong');

	// JavaScript
	var p = document.querySelectorAll('p');
	p.forEach((value, index) => {
	  	var target         = value.textContent;
	  	var strong         = document.createElement('strong');
	  	strong.textContent = target;
	  	p[index].innerHTML = strong.outerHTML;
	});

### 去除父元素
	<strong><p id="first">Hello Rizu</p></strong>
	
	// jQuery
	$('p').unwrap();

	// JavaScript
	var target      = document.querySelector('#first');
	var parent      = target.parentNode;
	var grand       = parent.parentNode;
	grand.innerHTML = target.outerHTML;

### 使用其他元素替换指定元素
	<p id="first">Hello Rizu</p>
	
	// jQuery
	$('p').replaceWith('<h1>替换后</h1>');

	// JavaScript
	document.querySelector('#first').outerHTML = '<h1>替换后</h1>';

### 删除元素
	<p id="first"><strong>删除的元素</strong>Hello Rizu</p>
	
	// jQuery
	$('p strong').remove();

	// JavaScript
	var target = document.querySelector('#first');
	var nest   = document.querySelector('#first strong');
	target.removeChild(nest);

### 获取与修改属性值
	<a href="http://yrq110.me/">blog</a>
	
	// jQuery
	$('a').attr('href', "http://developer.mozilla.org ");
	$('a').text($('a').attr('href'));

	// JavaScript
	document.querySelector('a').setAttribute('href', "http://developer.mozilla.org ");
	var target         = document.querySelector('a');
	target.textContent = target.getAttribute('href');

### 删除属性值
	<a href="http://yrq110.me/" target="_blank">blog</a>
	
	// jQuery
	$('a').removeAttr('target');

	// JavaScript
	document.querySelector('a').removeAttribute('target');

### class值的添加与删除
	<p>Hello Rizu</p>
	
	// jQuery
	$('p').addClass('red');
	$('p').removeClass('red');

	// JavaScript
	var target = document.querySelector('p');
	target.classList.add('red');
	target.classList.remove('red');

### 设置多个CSS属性值(CSS in JS)
	<p>Hello Rizu</p>
	
	// jQuery
	$('p').css({
	  	'color': 'red',
	  	'border': '1px solid black'
	});

	// JavaScript
	document.querySelector('p').style.color  = 'red';
	document.querySelector('p').style.border = '1px solid black';

### 点击事件
	<p>Hello Rizu</p>
	
	// jQuery
	$('p').click(function() {
	  	$(this).css('color', 'red');
	});

	// JavaScript
	document.addEventListener('click', () => {
	  	document.querySelector('p').style.color = 'red';
	}, false);

## 距离
### 滚动距离
	// jQuery
	$(window).scrollTop();
	$(window).scrollLeft();

	// JavaScript
	document.body.scrollTop || document.documentElement.scrollTop;
	document.body.scrollLeft || document.documentElement.scrollLeft;

### 获取元素的宽度，高度（不包含padding, border, margin）
	// jQuery
	$('#box').width();
	$('#box').height();
	
	// JavaScript
	// 暂无
	
### 获取元素的宽度，高度（包含padding，不包含border, margin）
	// jQuery
	$('#box').innerWidth();
	$('#box').innerHeight();
	
	// JavaScript
	document.querySelector('#box').clientWidth;
	document.querySelector('#box').clientHeight;
	或者
	document.querySelector('#box').scrollWidth;
	document.querySelector('#box').scrollHeight;
	
### 获取元素的宽度，高度（包含padding, border，不包含margin）
	// jQuery
	$('#box').outerWidth();
	$('#box').outerHeight();
	
	// JavaScript
	document.querySelector('#box').offsetWidth;
	document.querySelector('#box').offsetHeight;
	
### 获取元素的宽度，高度（包含padding, border，margin）
	// jQuery
	$('#box').outerWidth(true);
	$('#box').outerHeight(true);
	
	// JavaScript
	// 暂无

### 获取元素边框的厚度
	// jQuery
	// 无相关写法，不过可以计算出来（左边框和有边框相等，上边框和下边框相等时才正确）
	($('#box').outerWidth()-$('#box').innerWidth())/2;
	($('#box').outerHeight()-$('#box').innerHeight())/2;
	
	// JavaScript
	// 左边框，上边框的厚度
	document.querySelector('#box').clientLeft;
	document.querySelector('#box').clienttop;
	
### 相对距离
	// jQuery
	// 对象距离window的左边距、上边距
	$('#box').offset().left;
	$('#box').offset().top;

	// JavaScript
	// 对象距离最近定位属性的父级的左边距、上边距，如果都没有定位属性那默认为window
	document.querySelector('#box').offsetLeft;
	document.querySelector('#box').offsetTop;

### 
	// 对象style属性上的left,top值（如果left，top都有值的情况）
	$('#box').position().left;
	$('#box').position().top;

## 未完待续

## 参考
yrq110的[jQuery->JavaScript一览表](http://yrq110.me/2017/09/15/20170915-jquery-js-table/)
