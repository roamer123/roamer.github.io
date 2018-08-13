# 组件化和react

- 说下对组件化的理解

    封装-视图，数据，变化逻辑

    复用-

- jsx的本质

  * jsx语法

     html

     js表达式，判断，循环，事件绑定

     style和className

  * jsx解析成js

	  jsx其实是语法糖

	  开发环境会将jsx编译成js, vue2.0后，vue模版会变编译成render函数

	  jsx的写法大大降低了学习成本和编码工作量

	  同时，jsx会增加debug成本

  * 独立的标准

      jsx是react引入，但不是react独有的

      react已经将它作为独立标准开放，其他项目也可用

      react.createElement是可以自定义修改的，vdom h

      说明：本身功能已经完备，和其他标准兼容和扩展性没问题

- jsx和vdom

  分析：为何需要vdom

    解答：jsx需要渲染成html，数据驱动视图，

    vdom是react初次提出推广开的，结合jsx

    jsx就是模板，最终钥渲染成html

    初次渲染 + 修改state后的re-render

    正好符合vdom的应用场景

  React.createElement和h

    解答： 都会生成vnode, React.createElement第一参数有可能是字符串和自定义组件（构造函数）

  何时patch

    初次渲染-ReactDOM.render(<App/>, container); => 触发 _patch(vNode, container)

    re-render - setState => 触发 _patch(vNode, newVnode)

  自定义组件的解析

     初始化实例，然后执行render

- React setState的过程

  setState的异步

      为什么？

         * 可能会一次执行多个setState,

         * 无法规定，限制用户使用setState,

         * 考虑性能不必每次重新渲染

         * 即便每次重新渲染，用户看不到中间效果，只看到最后结果即可

  vue修改属性也是异步

     效果，原因和setState一样

  setState的过程

      每个组件实例，都有renderComponent方法

      执行renderComponent会重新执行实例的render

      render函数返回newVnode，然后拿到preVnode

      执行patch(vNode, newVnode)

- react和vue的选型

    模版的区别

       vue使用模板（最初由angular）

       React 使用jsx

       模版语法 -react

       模版分离 -vue

    共同点

       都支持组件化

       数据驱动视图

    国内使用，首推vue,文档更易读，易学，社区够大

    团队水平较高，推荐使用React，组件化和jsx




