# 异步

- 什么是单线程，和异步由什么关系

  * 同一时间只能做同一件事情，原因：避免渲染的冲突。 解决方案：异步。

- 什么是event-loop

  * 同步代码立即执行，异步函数在异步队列中不立即执行，主进程执行完成后在执行异步队列。

  * 事件轮询，js实现异步的具体解决方案。

  * 同步代码直接执行，异步函数先放在异步队列中，有延时时间的等延时时间结束后在放入，等同步函数执行完毕后，轮询执行异步队列函数

  * 何时放入异步队列

  轮询策略

- 是否用过jQuery的Deferred

  * jQuery1.5之后使用Deferred,ajax的使用

  * 说明如何简单封装，使用Deferred，开放封闭原则

  * 说明promise和Deferred的区别，promise主要用于监听

- Promise的基本使用和原理

  * 基本语法，异常捕获（throw Error和reject，多个reject通过catch统一捕获），多个串联（then中返回新的Promise），Promise.all和Promise.race, Promise标准

  * 关于“标准”的闲谈， 状态变化，then

       任何技术推广都需要标准支持，无规矩不成方圆，任何不符合标准的东西，将会被用户抛弃，不要挑战标准，不要自造标准。

       三种状态：pending, fulfilled, rejected, 初始状态： pending, pending->fulfilled, pending->rejected

       Promise实例必须实现then， 返回的是一个Promise， 接收2个函数

- async/await thunk

  * 基本用法 await后加Promise， async/await

  * 完全是同步写法，没有callback

  * 任何写法改变不了js单线程和异步的本质

- 当前js解决异步方案

  jquery Deferred, Promise, async/await, generator