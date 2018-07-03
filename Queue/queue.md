### 还是先创建一个节点

```javascript
function Node(value) {
  this.value = value;
  this.pointer = null;
}
```
节点的结构和栈的结构一样 都是有一个保存节点的值的value和一个指针pointer，只不过这个pointer值较早加入的节点指向较晚加入的节点的。

### 有了节点就可以写一个队列了

```javascript
function Queue() {
  this.start = null;
  this.end = null;
}
```
好吧这里也和栈很类似，就不多作解释了。

### 加入节点的方法

```javascript
function Queue() {
  this.start = null;
  this.end = null;
  
  this.push = function (value) {
    let node = new Node(value);
    if (this.end) {
      this.end.pointer = node;
      this.end = node;
    } else {
      this.start = node;
      this.end = node;
    }
  }
}
```
插入节点时，先判断一下队列里有没有节点，如果没有的话，就把头指针和尾指针都指向这个节点，如果没有的话，就先把最后一个节点的pointer指向新加入的节点。
然后再把尾指针指向新加入的节点。

### 弹出节点的方法（先进先出）
```javascript
function Queue() {
  this.start = null;
  this.end = null;
  
  this.push = function (value) {
    let node = new Node(value);
    if (this.end) {
      this.end.pointer = node;
      this.end = node;
    } else {
      this.start = node;
      this.end = node;
    }
  }
  
  this.pop = function () {
    let node = null;
    if (this.start) {
       node = this.start;
       this.start = this.start.pointer;
       if (this.start.ponter === null) {
        this.end = null;
       }
    }
    return node;
  }
}
```
弹出的时候一定要注意先先进先出，所以我们先从start指针开始，每次弹出start的值时，将start的指向start的pointer，也就是相对于较晚一次加入的节点，
直到，pointer变为null时，也就没有节点了。
