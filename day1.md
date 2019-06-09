##  ES6

### 声明变量

> const

1. 声明常量（不能再次修改值，引用类型不能修改地址）
2. {}会产生块级作用域 
    es5之前只有函数作用域 
3. 不会变量提升
4. const 不能在声明时不赋值
5. const 声明不能重名

> let

1.声明变量 let const var 不能同时出现
2.暂时性死区  也没有变量提升 会产生块级作用域
3.在同一作用域内不能产生相同变量
4.es6明确规定在当前作用域下使用let和const声明变量在该变量之前不允许赋值，会形成一个暂时性死区

** var声明的变量会变成顶层对象的属性  **  

** let和const生产的变量不会被挂在到顶层对象中 **

####  Object

1.Object.defineProperty(obj,prop,descriptor) 
    {
        obj:要在其上定义属性的对象
        prop:要定义或修改的属性的名称。
        descriptor:将被定义或修改的属性描述符
    }
2.属性描述符:{
    value:当前属性值
    enumberable:可枚举  ture  false
    configurable:可配置  ture  false
    writable:可编辑  ture  false
}
{
    当前属性变成访问器属性
    get(){
        
    }
    set{
        
    }
}

#### 箭头函数
写法:()=>{}

箭头函数和普通函数的区别

this指向不同，箭头函数this指向始终指向定义该的对象

#### 事件代理

let proxy = new Proxy(target, handler);

参数:target 是用 Proxy 包装的目标对象（可以是任何类型的对象，包括原生数组，函数，甚至另一个代理）, 参数 handler 也是一个对象，其属性是当执行一个操作时定义代理的行为的函数，也就是自定义的行为

具体写法:
 let obj = {}
 let proxyObj = new Proxy(obj,{
     get (target,key) {
        console.log('target...',target,key)
     },
     set (target,key,value) {
        console.log('target...',target,key,value)
     }
})


####  Promise

异步:async/await  Promist  generator

promise描述:promise是异步编程的一种解决方案，可以将异步操作以同步操作的流程表达出来,
避免了层层嵌套的回调函数

promise的三种状态:

1.pending 正在加载 
2. fulfilled 成功
3. rejected 失败
  pending -> fulfilled
  pending ->rejected

promise两种静态方法(用这两种方法可以继续链式调用):

1.resolve
2.reject

代码案例:
//图片懒加载
functio loadImg(url){
    return  new Promise((resolve,reject)=>{
         var image = new Image();
        image.onload = function () {
            resolve(image);
        }
        image.onerror = function () {
            reject(new Error('Could not load image at '+url))
        }
        image.src = url
    })
}
loadImg('图片地址').then(res=>{
    document.body.appendChildren(res)
},err=>{
    console.log('err',...err)
})













