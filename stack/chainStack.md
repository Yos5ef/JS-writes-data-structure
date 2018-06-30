# 栈结构
## 链式栈

```javascript
function Node(value){
  this.pointer = null;
  this.value = value;
}
function Stack(){
  this.top = null;
  this.bottom = null;
  this.push = function(value){
    let node = new Node(value);
    if(this.top != null){
      node.pointer = this.bottom;
      this.bottom = node;
    }else{
      this.top = node;
      this.bottom = node;
    }
  }
  this.pop = function(){
    if(this.bottom){
      let node = null;
      node = this.bottom;
      this.bottom = this.bottom.pointer;
      return node.value;
    }
  }
}


//test
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
