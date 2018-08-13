# vitural DOM

- vdom是什么，为何为存在vdom

  * 用js模拟DOM结构，

  * DOM操作非常“昂贵”

  * 将DOM对比操作放在JS层，提供效率

	  提供重绘性能,DOM操作是“昂贵”的，js运行效率高

	  减少DOM操作，而不是“推倒重来”

	  dom操作回收，重复绑定函数

	  jquery实现遇到的问题

- vdom如何应用，核心API

  * 介绍snabbdom

    h(dom+selector, props, content);

    patch(container, vnode);  // patch into empty element, this modifies the DOM as 

    a side effect

    patch(vnode, newVnode); // second `patch` invocation Snabbdom efficiently the 

    old view to the new state

    ```
       var patch = snabbdom.init([
           snabbdom_class,
           snabbdom_props,
           snabbdom_style,
           snabbdom_eventListeners,
       	]);

       	var h = snabbdom.h;

       	var container = document.getElementId('container');

       	var vnode = h('ul#list', {}, [
            h('li.item', {}, 'Item1'),
            h('li.item', {}, 'Item2'),
       	]);

       	patch(container, vnode);

       	document.getElementId('btn-change').addEventListener('click', function(){

       		var newVnode = h('ul#list', {}, [
	            h('li.item', {}, 'Item1'),
	            h('li.item', {}, 'ItemB'),
	            h('li.item', {}, 'Item3'),
	       	]);
	       	patch(vnode, newVnode);
       	});

    ```

  * 核心API

    h('标签名'， {..props}, [子元素])

    h('标签名'， {..props}, '...')

    patch(container, vnode);

    patch(vnode, newVnode);


- 介绍下diff算法

   什么是Diff算法， vDOM为何用Diff算法，diff算法的实现

   是Linux的基础命令， git diff

   vdom中的应用diff算法是为了找出需要更新的节点。

   两个patch

	   节点的新增和删除，节点重新排序，节点属性，样式，属性绑定， 如何极致压榨性能。。。

	   两个patch的形式，createElement, updateElement




