# 栈结构
## 链式栈

链式栈顾名思义 就是就是每个节点之间都有一个"链"相连的 ，我们首先要创建一个节点

```javascript
function Node(value) {
	this.pointer = null;
	this.value = value;
}
```

我们用pointer属性来表示链接各个节点的“链” value属性表示节点的内容。

已经有了节点了 我们接下来所要做的事就是把这些节点连接起来变成一个栈了，我们前面讲到栈结构，就像压盘子一样，先进后出。所以我们要写两个指针。top 和 bottom 用来指向最底下的盘子和最上面的盘子。

```javascript
function Stack() {
	this.top = null;
	this.bottom = null;
}
```
有了top指针和bottom指针，我们就可以压盘子（压栈）了,添加一个push方法了来表示这个操作

```javascript
function Stack() {
	this.top = null;
	this.bottom = null;
	this.push = function (value) {
		let node = new Node(value);
		if (this.top !== null) {
			node.pointer = this.bottom;
			this.bottom = node;
		} else {
			this.top = node;
			this.bottom = node;
		}
	}
}
```
在调用Stack中的push方法时，会传入一个value座位节点的值，每次传入时都会先判断一下top是否为空 如果为空的话 证明还没有盘子，我们就可以把这个push进的盘子放在最底下，这时只有一个盘子，所以top和bottom都指向这个节点。如果不为空的话，就证明已经才在盘子了，所以放在存在的上一次加入的盘子的上方，所以先把新加入的节点的指针，指向上一次刚刚加入的节点也就是bottom,再把bottom指向最后一位

有了盘子和压盘子的方法，我们就该写拿盘子的方法也就是弹栈了：

```javascript
function Stack() {
	this.top = null;
	this.bottom = null;
	this.push = function (value) {
		let node = new Node(value);
		if (this.top !== null) {
			node.pointer = this.bottom;
			this.bottom = node;
		} else {
			this.top = node;
			this.bottom = node;
		}
	}
	this.pop = function () {
		if (!top) return;
		let node = null;
		node = this.bottom;
		this.bottom = this.bottom.pointer;
		return node.value;
	}
}
```
弹栈就比较好理解了。判断一下有没有盘子可以拿，如果有，我们就把这个盘子拿到，然后把bottom往下指一位，这个节点就不存在这个栈里了。

最后写一个方法测试一下吧。

```javascript
let arr = [1,2,3,4,5,6,7,8,9,0];
let stack = new Stack();
for(let i=0,len=arr.length;i<len;i++){
	stack.push(arr[i]);
}
for(let i=0;i<10;i++){
	let a = stack.pop();
	alert(a);
}
```
[最终代码](https://github.com/Yos5ef/JS-writes-data-structure/blob/master/stack/chainStack.js)





