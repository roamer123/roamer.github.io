# ES6

## questions

- ES6模块化如何使用，开发环境如何打包

  模块化基本语法：export default ／ export ／

  开发环境配置：babel .babelrc webpack rollup单一职责只做打包(rollup全家桶, babelrc, rollup.config.js), wangEditor(gulp + rollup)

  众多模块化标准: commonJs-后端, AMD(require.js define), CMD

- Class和普通构造函数有何区别

  js构造函数

  class基本语法

  语法糖

      typeof ExampleContruClass // function.
	  ExampleContruClass.prototype.constructor = ExampleContruClass //true
	  const e = new ExampleContruClass();
	  m.__proto__ === ExampleContruClass.prototype // true 显式原型等于隐式原型

	  证明Class就是语法糖，其本质和ES5的构造函数无区别。

  继承


- Promise基本使用和原理

- ES6常用功能