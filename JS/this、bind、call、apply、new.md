## 关于 this 的指向

1. 全局作用域下，this 指向 window

2. 函数中，this 的指向和函数的调用方式有关
   1. 作为对象的熟悉被调用时，this 的执行为调用该函数的对象
   2. 作为普通函数调用时，this 指向 window，严格模式下指向 undefined
   3. 作为箭头函数调用时，this 指向箭头函数外层作用域
   4. 作为 call bind apply 等调用时，this 指向其第一个参数
   5. 作为构造函数调用时，this 执行新创建的对象





## 箭头函数



## bind、call、apply



## new 关键词

- 创建一个空对象，this 引用该对象，同时继承该对象的原型
- 属性和方法添加到 this 引用的对象中
- 新场景的对象由 this 引用，并且隐式的返回 this



```js
// 手写实现 new 操作符的功能
function Person(name, age) {
    this.name = name;
    this.age = age;
}
Person.prototype.say = function () {
    console.log("say");
};

function myNew(fn, ...args) {
    // 1. 创建一个空对象
    // // 2. 设置原型链
   
    let obj = Object.create(fn.prototype);
    // 3. 绑定this
    let result = fn.apply(obj, args);
    // 4. 返回对象
    return result instanceof Object ? result : obj;
}

let p = myNew(Person, "张三", 18);
console.log(p);
p.say();
```





