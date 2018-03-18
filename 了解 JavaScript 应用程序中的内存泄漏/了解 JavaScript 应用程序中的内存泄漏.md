# 了解 JavaScript 应用程序中的内存泄漏

## 内存泄漏1：闭包

## 内存泄漏2：控制台日志
> 1.在用户键入JavaScript时，在控制台中的一个交互式会话期间记录的对象
> 
> 2.由console.log 和 console.dir 方法记录的对象。

## 内存泄漏3：循环
> 在两个对象彼此引用且彼此保留时，就会产生一个循环

摘自[IBM->Web development](https://www.ibm.com/developerworks/cn/web/wa-jsmemory/)