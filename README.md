# js学习笔记

## 原型链/继承

* javascript所有的对象都有一个隐藏的原型[[prototype]],这个原型要么是对象，要么是null
* obj._proto_方法可以获取对象原型
* 如果要获取对象的某个属性或者方法，但是这个对象本身没有，js就会从去对象的原型查找
* 如果对象的方法obj.method()中，这个方法来自原型，那么该方法中的this指向该对象
* for...in循环可以遍历obj自己的属性和原型的属性，但是别的方法比如obj.keys(),只能遍历对象自己的属性。

## 函数
* 函数传参，arguments是个类数组对象(ArrayLike),所以不能直接使用array,join()方法
```
	arguments instanceof Array  //false
	typeof arguments //Object
```
* 箭头函数没有this,没有arguments,不能通过new调用
## apply call bind

* 三者都是用来改变函数的this对象的指向的
* 三者第一个参数都是this要指向的对象，也就是想指定的上下文
* 三者都可以利用后续参数传参
* bind 是返回对应函数，便于稍后调用；apply 、call 则是立即调用。
* call 和 apply传参方法不一样
```
	func.call(context, ...args); // pass an array as list with spread operator
	func.apply(context, args);   // is same as using apply
	eg: obj1.func.call(obj2,1,2,3)  == obj1.func.call(obj2,...[1,2,3])
		obj1.func.call(obj2,1,2,3)  == obj1.func.apply(obj2,[1,2,3])
```
## 同域访问（domain/ports/protocl）