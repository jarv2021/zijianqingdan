##语法和API

###1.理解ECMAScript和JavaScript的关系

ECMAscript到底是什么？它和JavaScript的关系？
要讲清楚这个问题，需要回顾历史。1996年11月，JavaScript的创造者Netscape公司，决定将JavaScript提交给国际标准化组织ECMA，
希望这种语言能够成为国际标准。次年，ECMA发布262号标准文件（ECMA-262）的第一版，规定了浏览器脚本语言的标准，并将这种语言成为ECMAScript，这个版本就是1.0版。

该标准从一开始就是针对JavaScript语言制定的，但之所以不叫JavaScript，有两个原因。一是商标，Java是Sun公司的商标，根据授权协议，
只有Netscape公司可以合法地使用JavaScript这个名字，且JavaScript本身也已经被Netscape公司注册为商标。二是想体现这门语言的制定者是ECMA，
不是Netscape，这样有利于保证这门语言的开放性和中立性。因此，ECMAScript和JavaScript的关系是，前者是后者的规格（标准），
后者是前者的一种实现（另外的ECMAScript方言还有Jscript和ActionScript）。

在日常场合，这两个词是可以互换的。

###2.熟练运用es5、es6提供的语法规范

es5：https://www.cnblogs.com/liuyinlei/p/6101674.html

es6：
https://www.jianshu.com/p/acc3197df582
http://es6.ruanyifeng.com/

###3.熟练掌握JavaScript提供的全局对象（例如Date、Math）、全局函数（例如decodeURI、isNaN）、全局属性（例如Infinity、undefined）

参考书籍：javascript高级程序设计

###4.熟练应用map、reduce、filter 等高阶函数解决问题

参考资料：https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map#

###5.setInterval需要注意的点，使用settimeout实现setInterval

####setInterval需要注意的点

setInterval运行机制

setInterval的运行机制是，将指定的代码移出本次执行，等到下一轮Event Loop时，再检查是否到了指定时间。如果到了，就执行对应的代码；如果不到，就等到再下一轮Event Loop时重新判断。这意味着，setTimeout指定的代码，必须等到本次执行的所有代码都执行完，才会执行。

每一轮Event Loop时，都会将“任务队列”中需要执行的任务，一次执行完。setTimeout和setInterval都是把任务添加到“任务队列”的尾部。因此，它们实际上要等到当前脚本的所有同步任务执行完，然后再等到本次Event Loop的“任务队列”的所有任务执行完，才会开始执行。由于前面的任务到底需要多少时间执行完，是不确定的，所以没有办法保证，setTimeout和setInterval指定的任务，一定会按照预定时间执行。

这一点对于setInterval影响尤其大。

setInterval(function(){
  console.log(2);
},1000);

(function (){
  sleeping(3000);
})();
上面的第一行语句要求每隔1000毫秒，就输出一个2。但是，第二行语句需要3000毫秒才能完成，请问会发生什么结果？

结果就是等到第二行语句运行完成以后，立刻连续输出三个2，然后开始每隔1000毫秒，输出一个2。也就是说，
setIntervel具有累积效应，如果某个操作特别耗时，超过了setInterval的时间间隔，排在后面的操作会被累积起来，
然后在很短的时间内连续触发，这可能或造成性能问题（比如集中发出ajax请求）。

####使用settimeout实现setInterval

timerFun()

function timerFun(){

  //要执行的操作

  var timer=setTimeout(function(){

  timerFun()

  clearTimeout(timer)

  },2000)

}

###6.JavaScript提供的正则表达式API、可以使用正则表达式（邮箱校验、URL解析、去重等）解决常见问题

JavaScript提供的正则表达式API：https://blog.csdn.net/luyaran/article/details/82462687

js正则大全： https://www.jb51.net/article/43190.htm

###7.JavaScript异常处理的方式，统一的异常处理方案

参考资料：https://segmentfault.com/a/1190000011481099

Error对象

throw 和 Promise.reject() 可以抛出字符串类型的异常，而且可以抛出一个 Error 对象类型的异常。

一个 Error 对象类型的异常不仅包含一个异常信息，同时也包含一个追溯栈这样你就可以很容易通过追溯栈找到代码出错的行数了。

所以推荐抛出 Error 对象类型的异常，而不是字符串类型的异常。

Throw

throw expression;

throw 语句用来抛出一个用户自定义的异常。当前函数的执行将被停止（throw 之后的语句将不会执行），
并且控制将被传递到调用堆栈中的第一个 catch 块。如果调用者函数中没有 catch 块，程序将会终止。

Try / Catch

try {
   try_statements
}
[catch (exception) {
   catch_statements
}]
[finally {
   finally_statements
}]

ry/catch 主要用于捕捉异常。try/catch 语句包含了一个 try 块, 和至少有一个 catch 块或者一个 finally 块，下面是三种形式的 try 声明:

try...catch
try...finally
try...catch...finally
try 块中放入可能会产生异常的语句或函数

catch 块中包含要执行的语句，当 try 块中抛出异常时，catch 块会捕捉到这个异常信息，并执行 catch 块中的代码，如果在 try 块中没有异常抛出，这 catch 块将会跳过。

finally 块在 try 块和 catch 块之后执行。无论是否有异常抛出或着是否被捕获它总是执行。当在 finally 块中抛出异常信息时会覆盖掉 try 块中的异常信息。

window.onerror

通过在 window.onerror 上定义一个事件监听函数，程序中其他代码产生的未被捕获的异常往往就会被 window.onerror 上面注册的监听函数捕获到。并且同时捕获到一些关于异常的信息。

window.onerror = function (message, source, lineno, colno, error) { }
message：异常信息（字符串）
source：发生异常的脚本URL（字符串）
lineno：发生异常的行号（数字）
colno：发生异常的列号（数字）
error：Error对象（对象）
注意：Safari 和 IE10 还不支持在 window.onerror 的回调函数中使用第五个参数，也就是一个 Error 对象并带有一个追溯栈

try/catch 不能够捕获异步代码中的异常，但是其将会把异常抛向全局然后 window.onerror 可以将其捕获。

Promise中的异常

Promise中抛出异常
new Promise((resolve,reject)=>{
    reject();
})

Promise中捕捉异常
promiseObj.then(undefined, (err)=>{
    catch_statements
});
promiseObj.catch((exception)=>{
    catch_statements
})

####统一异常处理

代码中抛出的异常，一种是要展示给用户，一种是展示给开发者。

对于展示给用户的异常，一般使用 alert 或 toast 展示；对于展示给开发者的异常，一般输出到控制台。

在一个函数或一个代码块中可以把抛出的异常统一捕捉起来，按照不同的异常类型以不同的方式展示，对于。

需要点击确认的异常类型：
ensureError.js

function EnsureError(message = 'Default Message') {
    this.name = 'EnsureError';
    this.message = message;
    this.stack = (new Error()).stack;
}
EnsureError.prototype = Object.create(Error.prototype);
EnsureError.prototype.constructor = EnsureError;

export default EnsureError;

弹窗提示的异常类型：
toastError.js

function ToastError(message = 'Default Message') {
    this.name = 'ToastError';
    this.message = message;
    this.stack = (new Error()).stack;
}
ToastError.prototype = Object.create(Error.prototype);
ToastError.prototype.constructor = ToastError;

export default ToastError;

提示开发者的异常类型：
devError.js

function DevError(message = 'Default Message') {
    this.name = 'ToastError';
    this.message = message;
    this.stack = (new Error()).stack;
}
DevError.prototype = Object.create(Error.prototype);
DevError.prototype.constructor = DevError;

export default DevError;

异常处理器：
抛出普通异常时，可以带上 stackoverflow 上问题的列表，方便开发者查找原因。
errorHandler.js

import EnsureError from './ensureError.js';
import ToastError from './toastError.js';
import DevError from './devError.js';
import EnsurePopup from './ensurePopup.js';
import ToastPopup from './toastPopup.js';

function errorHandler(err) {
    if (err instanceof EnsureError) {
        EnsurePopup(err.message);
    } else if (err instanceof ToastError) {
        ToastPopup(err.message);
    }else if( err instanceof DevError){
        DevError(err.message);
    }else{
        error.message += ` https://stackoverflow.com/questions?q=${encodeURI(error.message)}`
        console.error(err.message);    
    }
}

window.onerror = (msg, url, line, col, err) => {
    errorHandler(err);
}

window.onunhandledrejection = event =>{
    errorHandler(event.reason);
};

export default errorHandler;


