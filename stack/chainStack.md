# 栈结构
## 链式栈

链式栈顾名思义 就是就是每个节点之间都有一个"链"相连的 ，我们首先要创建一个节点

```javascript
function Node(value) {
	this.pointer = null;
	this.value = value;
}
```


