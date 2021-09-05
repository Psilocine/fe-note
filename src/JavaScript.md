# JavaScript

⭐ 执行上下文/作用域链/闭包

❓ 介绍一下 js 的执行上下文

❓ 介绍一下 js 的作用域链

❓ 介绍一下 js 的闭包是什么，以及应用的场景

🤔 闭包就是那些可以访问自由变量的函数（自由变量就是在函数中使用，既不是函数参数又不是函数的局部变量的变量）

* 从理论角度讲，所有的函数都是闭包，因为 JS 是词法作用域，函数在创建的时候就把父级的执行上下文的变量对象保存到作用域链上
* 从实践角度讲，闭包函数指的是：
1. 创建它的上下文已被销毁，仍然存在的函数（比如内部函数从父级函数返回）
2. 引用自由变量的函数

---

⭐ this/call/apply/bind

❓ 介绍一下 js 的 this

❓ 如何改变 this 指向

❓ call、apply、bind 有什么区别

❓ 如何实现 call 和 apply
```javascript
🤔
// call 的实现
Function.prototype.call2 = function (ctx) {
    ctx = ctx || window;
    ctx._fn = this;

    const args = [];
    for (let i = 0; i < arguments.length; i++) {
        args.push(`arguments[${i}]`);
    }
    
    const reulst = ctx._fn(...args);
    // 删除函数
    delete ctx._fn;
    return result;
}

// apply 的实现
Function.prototype.bind2 = function (ctx, arr) {
    ctx = ctx || window;
    ctx._fn = this;

    let result;
    if (!arr) {
        result = ctx._fn();
    } else {
        result = ctx._fn(...arr);
    }

    // 删除函数
    delete ctx._fn;
    return result;
}
```

❓ 如何实现一个 bind

🤔
```javascript
Function.prototype.bind2 = function (ctx) {
    // 防止调用 bind 的不是函数
    if (typeof this !== 'Function') {
        throw new Error('bind is not callable');
    }
    const self = this;
    // 把 ctx 执行上下文参数排除
    const args = Array.prototype.slice.call(arguments, 1);
    // 空函数中转，防止修改 fBound.prototype 时也修改绑定函数的 prototype
    const fNOP = function () {};
    const fBound = function () {
        // 收集函数调用时传入的参数
        const bindArgs = Array.prototype.slice.call(arguments);
        // 构造函数时，this 指向 实例，将绑定函数的 this 指向该实例，可以让实例获得来自绑定函数的值
        // 普通函数时，this 指向 window， 将绑定函数的 this 指向 ctx
        return self.apply(this instanceof fNOP ? this : ctx, args.concat(bindArgs));
    }

    fNOP.prototype = this.prototype;
    fBound.prototype = new fNOP();

    return fBound;
}
```

❓ 如何实现一个 new

🤔
```javascript
function new2 () {
    const obj = new Object();
    // 约定入参的第一个参数为构造函数，splice 会改变原数组
    const Constructor = Array.prototype.splice.call(arguments, 0, 1)[0];
    // 实例的原型指向构造函数，这样 obj 就可以访问到构造函数的属性
    obj.__proto__ = Constructor.prototype;
    // 使用 apply 改变构造函数的 this 指向 obj，传入参数
    const ret = Constructor.apply(obj, arguments);
    // 构造函数可能返回对象，如果是对象就返回该对象
    return typeof ret === 'object' ? ret : obj;
}

```

---

⭐ 原型/继承

❓ 介绍一下 js 的原型

❓ 原型链是什么

❓ 如何利用原型链实现继承

---

⭐ Promise

❓ Promise 是什么

🤔 Promise 是一种异步编程的解决方案，它有 Pending、Fulfilled、Rejected 三种状态。

❓ 如何实现一个 Promise

❓ Async await

---

⭐ 深浅拷贝

❓ 介绍一下 js 的深浅拷贝

❓ 如何实现浅拷贝

❓ 实现深拷贝需要注意哪些问题

❓ 如何解决循环引用的问题

---

⭐ 事件机制/event loop

❓ 如何实现一个事件的发布订阅

❓ 介绍一下事件循环

❓ 宏任务和微任务有什么区别

---

⭐ 函数式编程

❓ Service worker

❓ Web worker

❓ 介绍常用方法：数组方法、es6 后的方法
