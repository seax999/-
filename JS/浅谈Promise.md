# 浅谈 Promise



> ### **Promise的状态**

1. padding：进行中状态，刚创建且未改变状态的Promise
2. fulfilled：成功
3. reject：失败



​	promise 有三个状态，状态一经确定就不允许修改



> ### **Promise 的链式调用**

```js
/**
默认状态下，不改变状态的话，promise 返回的就是 padding 状态
[[Prototype]]: Promise
[[PromiseState]]: "pending"
[[PromiseResult]]: undefined
*/
const pro = new Promise((resolve, reject)=>{})

// .then 根据 promise 实例的状态去执行对应的操作，fulfilled 状态执行 resolve 函数，rejected 状态执行 reject 函数
const pro = new Promise((resolve, reject)=>{
    resolve()
})
pro.then(res=>{
    console.log('resolve'); // resolve
}, err=>{
    console.log('reject')
})

// 第一个 .then 默认状态返回一个状态为 fulfilled 的 promise 实例，如果 resolve/reject 函数没有返回新的 promise 实例，会一直返回 fulfilled 状态 
const pro = new Promise((resolve, reject)=>{
    reject()
})
pro.then(res=>{
    console.log('resolve'); 
}, err=>{
    console.log('reject');	// reject
}).then(res=>{
    console.log("resolve1");	// resolve1
}, err=>{
	console.log('reject1')
})

// .catch 会捕获 promise 执行过程中的异常
const pro = new Promise((resolve, reject)=>{
    throw new Error("12333");
})
pro.then(res=>{
    console.log('resolve'); 
}, err=>{
    console.log(err, ' reject');	// 12333 reject
})

// .catch 同样会捕获 rejected 状态但是没有接收 reject 函数的情况
// 即如果实例状态改成 rejected 之后，但是 .then 没有接收 reject 函数，则会抛出异常走到 .catch 里面
const pro = new Promise((resolve, reject)=>{
    reject()
})
pro.then(res=>{
    console.log('resolve'); 
}).catch(err=>{
    console.log(err, ' reject');	// reject
})
```



> ### **Promise 的扩展函数**

- ###### Promise.all()

​	Promise.all 接收一个 Promise 的可迭代实例数组，并且返回一个 promise 实例，

​	当传入的实例数组全部兑现成功的时候，返回所有兑现值的数组

​	一旦有一个失败，则返回第一个失败的实例失败原因，同时其他的实例依旧执行兑现

​	如果传入的是一个空数组，则直接成功，并且返回空数组

```js
const pro1 = new Promise((resolve, reject)=>{
	resolve(1)
})
const pro2 = new Promise((resolve, reject)=>{
	resolve(2)
})

// 接受一个空数组，则 resolve 接收一个空数组
Promise.all([]).then(res=>{
    console.log(res);	// []
})

// 传入的 promise 实例全部兑现执行成功，则 resolve 接收实例的兑现执行结果 [1,2]
Promise.all([pro1, pro2]).then(res=>{
    console.log(res);	// [1,2]
})

// 一旦有实例兑现执行失败，则直接走 reject 函数，入参为第一个实例执行失败传入的参数
const pro3 = new Promise((resolve, reject)=>{
	setTimeout(()=>{
        reject(3)
    },100)
})
const pro4 = new Promise((resolve, reject)=>{
	setTimeout(()=>{
        reject(3)
    },300)
})
Promise.all([pro3, pro4]).then(res=>{
    console.log(res);	
}, err=>{
	console.log(err); 	// 3
})
```



- ###### Promise.any

​	Promise.any 接收一个 Promise 的可迭代实例数组，并且返回一个 promise 实例，

​	当传入的实例数组中有任意一个兑现成功的话，返回第一个兑现成功的值，同时其他的实例依旧执行兑现，但是不影响结果。

​	全部失败则返回 AggregateError

​	如果传入的是一个空数组，则直接失败，并且返回空数组



- ###### Promise.race

​	Promise.race 接收一个 Promise 的可迭代实例数组，并且返回一个 promise 实例，

​	当传入的实例数组中有任意一个兑现了的话，也就是状态敲定了，即第一个兑现成功的话，返回的 promise 也会成功，第一个兑现失败的话，返回的 promise 也会失败，同时其他的实例依旧执行兑现，但是不影响结果

​	如果传入的是一个空数组，则会持续待定；如果传入的是非空但是不是 promise 实例的话，则异步敲定成功
