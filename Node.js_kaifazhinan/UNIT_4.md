# 第4章 Node.js核心模块
## 4.1 全局对象（Global Object）
注：永远使用var定义变量以免引入全局变量，因为全局变量会污染命名空间，提高代码的耦合风险。
### 4.1.2 process
* process是一个全局变量，即global对象的属性。
* process.argv是命令行参数数组
* process.stdout是标准输出流
* process.stdin是标准输入流
* process.nextTick(callback)的功能是为事件循环设置一项任务。Node.js会在下次循环调响应时调用callback。目的将复杂的工作拆散变成一个个较小的事件，尽量缩短每个事件的执行时间。
* 注：更多的内容详见http://nodejs.org/api/process.html
### 4.1.3 console
* console用于提供控制台标准输出。
* console.log()：向标准输出流打印字符并以换行符结束。
* console.error()：标准错误流输出。
* console.trace()：向标准错误输出当前的调用栈。
## 4.2 常用工具uitl
功能：提供常用函数的集合，用于弥补JS的功能过于精简的不足。
1. uitl.inheris(construtor,superConstructor)是一个实现对象间原型继承的函数。
* 注：constructior只能继承superConstructor在原型中定义的函数，而构造函数内部创造的属性和函数没有被继承。
2. uitl.inspect(object,[showHidden],[depth],[colors])是将一个任意对象转换为字符串的方法，通常用于调试和错误输出。
* 注：更多的内容详见http://nodejs.org/api/util.html
## 4.3 事件驱动events
Node.js的基石，因为Node.js本身架构是事件式，events提供了唯一的接口，不仅用于用户代码与Node.js下层事件循环的交互，还几乎被所有的模块依赖。
### 4.3.1 事件发射器
events模块唯一提供的一个对象：events.EventEmitter。
* EventEmitter.om(event,listener)；为指定的事件注册一个监听器
* EventEmitter.emit(event,[arg1],[arg2],[...])；发射event事件，传递参数
* EventEmitter.once(event,listener)；为指定的事件注册一个单次监听器
* EventEmitter.removeListener(event,listener)；移除指定的事件的某个监听器
* EventEmitter.removeAllListener([event])；移除所有的事件的所有监听器
* 注：更多的内容详见http://nodejs.org/api/events.html
### 4.3.2 error事件
EventEmitter.emit('error').
## 4.3.3 继承EventEmitter
大多数不会直接使用EventEmitter，而是在对象中继承EventEmitter。
## 4.4 文件系统fs
fs模块是文本操作的封装，提供了文件的读取、写入、更名、删除、遍历目录、链接等POSIX文件系统操作，均有异步和同步两个版本。
* fs所有函数的定义和功能详见表4-1
## 4.5 HTTP服务器与客户端
封装了一个高校的HTTP服务器和一个简易的HTTP客户端。

