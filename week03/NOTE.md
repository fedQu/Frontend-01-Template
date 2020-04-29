# 每周总结可以写在这里

1. 对象有__proto__属性，函数有prototype属性；
2. 对象由函数生成;
3. 生成对象时，对象的__proto__属性指向函数的prototype属性。

没有修改__proto__默认的通用规则

原型链图：

![img](file:///D:/doc/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/m18811484968@163.com/e20beb4f907640938f0bb7eef592a03e/clipboard.png)

<script type="text/javascript">

  class Point {

​    constructor() { // 指向构造函数Point

​    }

​    todo() { // 原型方法

​    }

  }

  let point = new Point();

  console.log(point.prototype) // 实例对象没有prototype属性 可以直接通过constructor读取到构造函数

  console.log(point.__proto__)

  // 内部定义的方法是不可枚举的，与es5是不一样的

  // constructor方法是必须要有的，如果没有显示定义，则会默认添加一个空的constructor() {}

  const proObj = {

​    a: 1, b: 2,

  }

  console.log('obj', Object.create(proObj).__proto__);

  // js一切皆是对象，分为两类对象和函数

  // js原型链的通用规则：

  // 对象有__proto__属性，函数有prototype属性 对象是由函数生成的 对象生成时的__proto__属性向函数的prototype的属性

  // eg

  var o = {};

  console.log(o.__proto__ === Object.prototype) //or

  var o = Object(); // Object() 这是函数 ？它可以不用new嘛

  console.log(o.__proto__ === Object.prototype) 

  // 函数也是对象的一种，上面规则同样适用 eg

  function fn() {}; 

  console.log(fn.__proto__ === Function.prototype) 

  // Object 函数也是一种函数对象

  console.log(Object.__proto__ === Function.prototype)

  // prototype 

  // 对象的__proto__是生成它的函数的prototype得来的

  // 函数的prototype属性是系统生成的类型为object的对象，有两个属性constructor和__proto__, 

  // constructor是指自身，__proto__指向Object.prototype,

  // 说明函数的原型对象是由Object函数生成的 eg

  function foo() {}

  console.log(foo.prototype)

  console.log(foo.prototype.__proto__ === foo.__proto__) // false

  console.log(foo.prototype.__proto__) // 指向Object.prototype

  console.log(foo.__proto__) // 指向Function.prototype

  // console.log(foo.prototype.__proto__) ???

  // 特殊情况 特殊函数就是Object和Function函数

  // Object.prototype 也是一个类型为object的对象 多了一推系统默认的方法 没有__proto__属性了，打印出来为null 

  // Object.prototype.__proto__ 是js原型链的终点了 规定值为null

  console.log(typeof Function.prototype) // 是一个function的对象 

  console.log(Function.prototype.__proto__ === Object.prototype) // true 指向了Object的原型

  // sum

  // 这两个特殊情况，是为了让__proto__构成的原型链有个唯一的终点

</script>