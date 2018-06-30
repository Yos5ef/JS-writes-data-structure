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
      node = this.b
