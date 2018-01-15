# 第4章 Node.js核心模块
## 4.1 全局对象（Global Object）
注：永远使用var定义变量以免引入全局变量，因为全局变量会污染命名空间，提高代码的耦合风险。
### 4.1.2 process
* process是一个全局变量，即global对象的属性。
* process.argv是命令行参数数组
* process.stdout是标准输出流
* process.stdin是标准输入流
* process.nextTick(callback)的功能是为事件循环设置一项任务。Node.js会在下次循环调响应时调用callback。目的将复杂的工作拆散变成一个个较小的事件，尽量缩短每个事件的执行时间。
* 注：其他的使用可以访问http://nodejs.org/api/process.html
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
* 注：其他更多的使用可以访问http://nodejs.org/api/util.html
