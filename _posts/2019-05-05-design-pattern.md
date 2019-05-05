---
layout: post
title: 模块
subtitle:
date: 2019-05-05
tags: ['design-pattern']
---
## 链式调用

### 定义：
* 定义：通过为多个对象提供处理请求的机会，避免将请求的发送者耦合到其接收者。链接接收对象并沿链传递请求，直到对象处理它。
* 摘要：链接模式经常在JavaScript中使用（jQuery广泛使用此模式）


## 代码
```
var Request = function(amount) {
    this.amount = amount;
    log.add("Requested: $" + amount + "\n");
}
 
Request.prototype = {
    get: function(bill) {
        var count = Math.floor(this.amount / bill);
        this.amount -= count * bill;
        log.add("Dispense " + count + " $" + bill + " bills");
        return this;
    }
}
 
// log helper 
 
var log = (function() {
    var log = "";
 
    return {
        add: function(msg) { log += msg + "\n"; },
        show: function() { alert(log); log = ""; }
    }
})();
 
function run() {
    var request = new Request(378);
 
    request.get(100).get(50).get(20).get(10).get(5).get(1);
 
    log.show();
}
```


