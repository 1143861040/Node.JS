# 第3章 Node.js快速入门
## 3.2 异步式I/O与事件式编程
### 3.2.1 阻塞与线程
特点：控制流在很大程度上要靠事件与回调函数来组织，一个逻辑要拆分为若干个单元。采用**单线程，非阻塞的事件编程模式**。
* 同步式I/O（阻塞式I/O）
1. 线程在遇到I/O操作时，操作系统会剥夺CPU控制权，暂停执行，将资源让给其他的线程，当I/O操作技术时恢复其对CPU的控制权。（此种线程的调度方式称为**阻塞**）
2. 阻塞模式下提高吞吐量需要通过**多线程**。
* 异步式I/O（非阻塞式I/O）
1. 线程在遇到I/O操作时，将I/O请求发送给操作系统，继续执行下一条语句，当操作系统完成所有的I/O操作时，以**事件**的形式通知执行I/O的操作的线程，并在特定时间进行处理。
2. 必须有**事件循环**；一个线程永远在执行计算操作，CPU核心利用率为100%。
* 两者的特点:见表3-1
### 3.2.2 回调函数
eg:fs.readfile('file.txt','utf-8',**function(err,data)**{...}...
### 3.2.3 事件
事件是由EventEmitter对象提供。程序入口是事件循环的一个事件的回调函数。事件循环的原理见图3-5.
## 3.3 模块和包
### 3.3.2 创建及加载模块
模块与文件一一对应；包与目录一一对应。
1. 创建模块：exports是模块的公开接口。require用于从外部获取一个模块的接口，即获取模块的exports对象。
2. 加载模块：单次加载：不同的变量指向用一个实例，后面会将前面的覆盖。
3. 覆盖exports：exports本身是一个普通的空对象即{}，专门用来声明接口。eg:module.exports=Hello;
### 3.3.3 创建包
1. Node.js的包是一个目录，包含JSON格式的包说明文件package.json。包通常是一些模块的集合，相当于提供了一些固定接口的函数库。
2. Node.js调用包时会首先检查包中package.json文件中的main字段，作为包的接口模块。package.json是CommonJS规定用来描述包的文件。
### 3.3.4 Node.js包管理器（npm）
1. 获取一个包：
* 本地模式（默认）：eg：npm [install/i] [package_name]
    * 安装路径为当前目录的node_modules子目录下。可通过require使用，不需注册PATH。
* 全局模式：eg：npm [install/i] -g [package_name]
    * 安装路径为系统目录例如/usr/local/lib/node_modules/，同时package.json文件中的bin会被链接到/usr/local/bin/。不可通过require使用，需注册PATH。
2. 创建全局链接
* 功能：在本地包和全局包之间创建符号链接，使全局模式安装的包可以通过require使用。
* eg：npm link [package_name]  ./node_modules/[package_name]  ->  /usr/local/lib/node_modules/[package_name]（全局包当本地包使用）
* 注：npm link 命令不支持Windows。
3. 包的发布
* npm init；产生一个符合标准的package.json。
## 3.4 调试
1. 命令行调试（单步调试）：eg：node debug xutiaoshiwenjian.js;注：Node.js调试命令见表3-3
2. 远程调试：基于TCP协议，默认情况的调试端口是5858，可以通过--debug=1234将调试端口改成1234。
* eg：node --debug[=port] script.js；脚本会正常执行，不会暂停
* eg：node --debug-brk[=port] script.js；脚本暂停执行等待客户端连接
* 注：命令行调试实际上是将两步远程调试自动完成。
3. 使用Eclipse调试Node.js
* 具体安装步骤详见书中步骤
4. 使用node-inspector调试Node.js
* 具体安装步骤详见书中步骤

