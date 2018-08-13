# MVVM-vue

- 如何理解MVVM

  MVC 用户操作V，C同步到M， M更新V， 用户直接控制C，到M，到V

  MVVM M，V，VM。

      * VM-连接器   new vue({el: 'root', data: data; method: method})

      * DOM Listener V->VM->M

      * Data Bindings M->VM->V

- 如何实现MVVM

  关键是理解Object.defineProperty

- 是否解读过vue的源码



- 说下使用jQuery和使用框架的区别

  * jQuery工具类, vue框架,

     数据和视图的分离， 解耦（开放封闭原则）

     以数据驱动视图，只关心数据变化，DOM操作被封装（开发只希望更改数据，不去渲染页面）

- vue中如何实现响应式

   关键是理解Object.defineProperty

   将data的属性代理到vm上

    ```
    var mv = {};

	var data = {
		price: 100,
		name: 'dd';
	}

	var key, value
	for(key in data) {
		(function(key) {
		    Object.defineProperty(vm, key, {
		        get: function () {
		           return data[key];
		        },
		        set: function (newValue) {
		           data[key] = newValue;
		        }
		    })
		})
	}
	```

- vue中如何解析模版

    模板是什么

        * 本质是字符串

        * 有逻辑，如v-if v-for等

        * 与html格式很像，但有很大区别

        * 最终转换为html来显示

        * 模板最终必须转换为JS代码-render

    render函数

    ```
      <div id="app">
         <p>{{price}}<p>
      </div>


      with(this){
      	return _c{
      		'div',
      		{
      			attrs:{"id":"app"}
      		},
      		[
                _c('p', [_v(_s(price))])
      		]
      	}
      }
    ```

    v-model是怎么实现 - get set

    v-on:click 是怎么实现-绑定事件

    v-for是怎么实现- _l

    render函数与vdom _c 和 snabbdom的h相同

        updateComponent中实现了vdom的patch

        页面首次渲染执行updateComponent

        data中每次修改属性，执行updateComponent

	    render函数返回vnode

	    ```
	    vm._update(vnode) {
	    	const prevVnode = vm._vnode
	    	vm._vnode = vnode

	    	if(!prevVnode) {
	    		vm.$el = vm.__patch__(vm.$el, vnode)
	    	} else {
	    		vm.$el = vm.__patch__(prevVnode, vnode)
	    	}
	    }

	    function updateComponent(){
	    	//...
	        vm._update(vm._render());
	    }
	    ```

- vue的整个实现流程

    1. 解析模版成render函数

    2. 响应式开始监听

    3. 首次渲染显示页面，且绑定依赖

    4. data属性变化，触发rerender

- vue 三要素

* 响应式：vue如何监听到data的每个属性变化

    Object.defineProperty, 例子：修改data属性后，vue立刻监听到

    为什么要监听get？ 未走到get的属性，set的时候我们也无需关心，避免不必要的渲染

* 模版引擎：vue的模版如何被解析，指令如何处理

* 渲染：vue的模版如何被渲染成html，以及渲染过程。-首次渲染，rerender

