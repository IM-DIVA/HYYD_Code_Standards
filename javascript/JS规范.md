## JS规范

* 使用两个空格进行缩进。

```js
function hello (name) {
  console.log('hi', name)
}
```

* 除需要转义的情况外，**字符串统一使用单引号**。

```js
console.log('hello there')
$("<div class='box'>")
```

* **不要定义未使用的变量**。

```js
function myFunction () {
  var result = something()   // 错误
}
```

* **关键字后面加空格**。

```js
if (condition) { ... }   // 正确
if(condition) { ... }    // 错误
```

* **函数声明时括号与函数名间加空格**。

```js
function name (arg) { ... }   // 正确
function name(arg) { ... }    // 错误
 
run(function () { ... })      // 正确
run(function() { ... })       // 错误
```

* **始终使用 === 替代 ==。**
    例外： obj == null 可以用来检查 null || undefined。

```js
if (name === 'John')   // 正确
if (name == 'John')    // 错误
```
```js
if (name !== 'John')   // 正确
if (name != 'John')    // 错误
```

* **字符串拼接操作符 (Infix operators)** 之间要留空格。

```js
// 正确
var x = 2
var message = 'hello, ' + name + '!'
```
```js
// 错误
var x=2
var message = 'hello, '+name+'!'
```

* **逗号后面加空格。**

```js
// 正确
var list = [1, 2, 3, 4]
function greet (name, options) { ... }
```
```js
// 错误
var list = [1,2,3,4]
function greet (name,options) { ... }
```

* **else 关键字要与花括号保持在同一行。**

```js
// 正确
if (condition) {
  // ...
} else {
  // ...
}
```
```js
// 错误
if (condition)
{
  // ...
}
else
{
  // ...
}
```

* **多行 if 语句的的括号不能省。**

```js
// 正确
if (options.quiet !== true) console.log('done')
```
```js
// 正确
if (options.quiet !== true) {
  console.log('done')
}
```
```js
// 错误
if (options.quiet !== true)
  console.log('done')
```

* **不要丢掉异常处理中err参数**。

```js
// 正确
run(function (err) {
  if (err) throw err
  window.alert('done')
})
```
```js
// 错误
run(function (err) {
  window.alert('done')
})
```

* **使用浏览器全局变量时加上 window. 前缀**。
    Exceptions are: document, console and navigator.

```js
window.alert('hi')   // 正确
```

* **不允许有连续多行空行**。

```js
// 正确
var value = 'hello world'
console.log(value)
```
```js
// 错误
var value = 'hello world'
 
 
console.log(value)
```
* **对于三元运算符 ? 和 : 与他们所负责的代码处于同一行**。

```js
// 正确
var location = env.development ? 'localhost' : 'www.api.com'
 
// 正确
var location = env.development
  ? 'localhost'
  : 'www.api.com'
 
// 错误
var location = env.development ?
  'localhost' :
  'www.api.com'
```

* **每个 var 关键字单独声明一个变量**。

```js
// 正确
var silent = true
var verbose = true
 
// 错误
var silent = true, verbose = true
 
// 错误
var silent = true,
    verbose = true
```

* **条件语句中赋值语句使用括号包起来。这样使得代码更加清晰可读，而不会认为是将条件判断语句的全等号（===）错写成了等号（=）**。

```js
// 正确
while ((m = text.match(expr))) {
  // ...
}
 
// 错误
while (m = text.match(expr)) {
  // ...
}
```

* **单行代码块两边加空格**。

```js
function foo () {return true}    // 错误
function foo () { return true }  // 正确
```

* **对于变量和函数名统一使用驼峰命名法**。

```js
function my_function () { }    // 错误
function myFunction () { }     // 正确
 
var my_var = 'hello'           // 错误
var myVar = 'hello'            // 正确
```

* **不允许有多余的行末逗号**。

```js
var obj = {
  message: 'hello',   // 错误
}
```

* **始终将逗号置于行末**。

```js
  var obj = {
    foo: 'foo'
    ,bar: 'bar'   // 错误
  }
 
  var obj = {
    foo: 'foo',
    bar: 'bar'   // 正确
  }
```

* **点号操作符须与属性需在同一行**。

```js
  console.
    log('hello')  // 错误
 
  console
    .log('hello') // 正确
```

* **文件末尾留一空行**。

* **函数调用时标识符与括号间不留间隔**。

```js
console.log ('hello') // 错误
console.log('hello')  // 正确
```

* **键值对当中冒号与值之间要留空白**。

```js
var obj = { 'key' : 'value' }    // 错误
var obj = { 'key' :'value' }     // 错误
var obj = { 'key':'value' }      // 错误
var obj = { 'key': 'value' }     // 正确
```

* **构造函数要以大写字母开头**。

```js
function animal () {}
var dog = new animal()    // 错误
 
function Animal () {}
var dog = new Animal()    // 正确
```

* **无参的构造函数调用时要带上括号**。

```js
function Animal () {}
var dog = new Animal    // 错误
var dog = new Animal()  // 正确
```

* **对象中定义了存值器，一定要对应的定义取值器**。

```js
var person = {
  set name (value) {    // 错误
    this._name = value
  }
}
 
var person = {
  set name (value) {
    this._name = value
  },
  get name () {         // 正确
    return this._name
  }
}
```

* **子类的构造器中一定要调用 super**。

```js
class Dog {
  constructor () {
    super()   // 错误
  }
}
 
class Dog extends Mammal {
  constructor () {
    super()   // 正确
  }
}
```

* **使用数组字面量而不是构造器**。

```js
var nums = new Array(1, 2, 3)   // 错误
var nums = [1, 2, 3]            // 正确
```

* **避免使用 arguments.callee 和 arguments.caller**。

```js
function foo (n) {
  if (n <= 0) return
 
  arguments.callee(n - 1)   // 错误
}
 
function foo (n) {
  if (n <= 0) return
 
  foo(n - 1)
}
```

* **避免对类名重新赋值**。

```js
class Dog {}
Dog = 'Fido'    // 错误
```

* **避免修改使用 const 声明的变量**。

```js
const score = 100
score = 125       // 错误
```

* **避免使用常量作为条件表达式的条件（循环语句除外）**。

```js
if (false) {    // 错误
  // ...
}
 
if (x === 0) {  // 正确
  // ...
}
 
while (true) {  // 正确
  // ...
}
```

* **正则中不要使用控制符**。

```js
var pattern = /\x1f/    // 错误
var pattern = /\x20/    // 正确
```

* **不要使用 debugger**。

```js
function sum (a, b) {
  debugger      // 错误
  return a + b
}
```

* **不要对变量使用 delete 操作**。

```js
function sum (a, b, a) {  // 错误
  // ...
}
 
function sum (a, b, c) {  // 正确
  // ...
}
```

* **类中不要定义冗余的属性**。

```js
class Dog {
  bark () {}
  bark () {}    // 错误
}
```

* **对象字面量中不要定义重复的属性**。

```js
var user = {
  name: 'Jane Doe',
  name: 'John Doe'    // 错误
}
```

* **switch 语句中不要定义重复的 case 分支**。

```js
switch (id) {
  case 1:
    // ...
  case 1:     // 错误
}
```

* **同一模块有多个导入时一次性写完**。

```js
import { myFunc1 } from 'module'
import { myFunc2 } from 'module'          // 错误
 
import { myFunc1, myFunc2 } from 'module' // 正确
```
* **正则中不要使用空字符**。

```js
const myRegex = /^abc[]/      // 错误
const myRegex = /^abc[a-z]/   // 正确
```
* **不要解构空值**。

```js
const { a: {} } = foo         // 错误
const { a: { b } } = foo      // 正确
```
* **不要使用 eval()**。

```js
eval( "var result = user." + propName ) // 错误
var result = user[propName]             // 正确
```
* **catch 中不要对错误重新赋值**。

```js
try {
  // ...
} catch (e) {
  e = 'new value'             // 错误
}
 
try {
  // ...
} catch (e) {
  const newVal = 'new value'  // 正确
}
```
* **不要扩展原生对象**。

```js
Object.prototype.age = 21     // 错误
```
* **避免多余的函数上下文绑定**。

```js
const name = function () {
  getName()
}.bind(user)    // 错误
 
const name = function () {
  this.getName()
}.bind(user)    // 正确
```
* **避免不必要的布尔转换**。

```js
const result = true
if (!!result) {   // 错误
  // ...
}
 
const result = true
if (result) {     // 正确
  // ...
}
```
* **不要使用多余的括号包裹函数**。

```js
const myFunc = (function () { })   // 错误
const myFunc = function () { }     // 正确
```
* **switch 一定要使用 break 来将条件分支正常中断**。

```js
switch (filter) {
  case 1:
    doSomething()    // 错误
  case 2:
    doSomethingElse()
}
 
switch (filter) {
  case 1:
    doSomething()
    break           // 正确
  case 2:
    doSomethingElse()
}
 
switch (filter) {
  case 1:
    doSomething()
    // fallthrough  // 正确
  case 2:
    doSomethingElse()
}
```
* **不要省去小数点前面的0**。

```js
const discount = .5      // 错误
const discount = 0.5     // 正确
```
* **避免对声明过的函数重新赋值**。

```js
function myFunc () { }
myFunc = myOtherFunc    // 错误
```
* **不要对全局只读对象重新赋值**。

```js
window = {}     // 错误
```
* **注意隐式的 eval()**。

```js
setTimeout("alert('Hello world')")                   // 错误
setTimeout(function () { alert('Hello world') })     // 正确
```
* **嵌套的代码块中禁止再定义函数**。

```js
if (authenticated) {
  function setAuthUser () {}    // 错误
}
```
* **不要向 RegExp 构造器传入非法的正则表达式**。

```js
RegExp('[a-z')    // 错误
RegExp('[a-z]')   // 正确
```
* **禁止使用 __iterator__**。

```js
Foo.prototype.__iterator__ = function () {}   // 错误
```
* **外部变量不要与对象属性重名**。

```js
var score = 100
function game () {
  score: while (true) {      // 错误
    score -= 10
    if (score > 0) continue score
    break
  }
}
```
* **不要使用标签语句**。

```js
label:
  while (true) {
    break label     // 错误
  }
```
* **不要书写不必要的嵌套代码块**。

```js
function myFunc () {
  {                   // 错误
    myOtherFunc()
  }
}
 
function myFunc () {
  myOtherFunc()       // 正确
}
```
* **不要混合使用空格与制表符作为缩进**。

* **除了缩进，不要使用多个空格**。

```js
const id =    1234    // 错误
const id = 1234       // 正确
```
* **不要使用多行字符串**。

```js
const message = 'Hello \
                 world'     // 错误
```
* **new 创建对象实例后需要赋值给变量**。

```js
new Character()                     // 错误
const character = new Character()   // 正确
```
* **禁止使用 Function 构造器**。

```js
var sum = new Function('a', 'b', 'return a + b')    // 错误
```
* **禁止使用 Object 构造器**。

```js
let config = new Object()   // 错误
```
* **禁止使用 new require**。

```js
const myModule = new require('my-module')    // 错误
```
* **禁止使用 Symbol 构造器**。

```js
const foo = new Symbol('foo')   // 错误
```
* **禁止使用原始包装器**。

```js
const message = new String('hello')   // 错误
```
* **不要将全局对象的属性作为函数调用**。

```js
const math = Math()   // 错误
```
* **不要使用八进制字面量**。

```js
const num = 042     // 错误
const num = '042'   // 正确
```
* **字符串字面量中也不要使用八进制转义字符**。

```js
const copyright = 'Copyright \251'  // 错误
```
* **使用 __dirname 和 __filename 时尽量避免使用字符串拼接**。

```js
const pathToFile = __dirname + '/app.js'            // 错误
const pathToFile = path.join(__dirname, 'app.js')   // 正确
```
* **使用 getPrototypeOf 来替代 __proto__**。

```js
const foo = obj.__proto__               // 错误
const foo = Object.getPrototypeOf(obj)  // 正确
```
* **不要重复声明变量**。

```js
let name = 'John'
let name = 'Jane'     // 错误
 
let name = 'John'
name = 'Jane'         // 正确
```
* **正则中避免使用多个空格**。

```js
const regexp = /test   value/   // 错误
 
const regexp = /test {3}value/  // 正确
const regexp = /test value/     // 正确
```
* **return 语句中的赋值必需有括号包裹**。

```js
function sum (a, b) {
  return result = a + b     // 错误
}
 
function sum (a, b) {
  return (result = a + b)   // 正确
}
```
* **避免将变量赋值给自己**。

```js
name = name   // 错误
```
* **避免将变量与自己进行比较操作**。

```js
if (score === score) {}   // 错误
```
* **避免使用逗号操作符**。

```js
if (doSomething(), !!test) {}   // 错误
```
* **不要随意更改关键字的值**。

```js
let undefined = 'value'     // 错误
```
* **禁止使用稀疏数组（Sparse arrays）**。

```js
let fruits = ['apple',, 'orange']       // 错误
```
* **不要使用制表符**。

* **正确使用 ES6 中的字符串模板**。

```js
const message = 'Hello ${name}'   // 错误
const message = `Hello ${name}`   // 正确
```
* **使用 this 前请确保 super() 已调用**。

```js
class Dog extends Animal {
  constructor () {
    this.legs = 4     // 错误
    super()
  }
}
```
* **用 throw 抛错时，抛出 Error 对象而不是字符串**。

```js
throw 'error'               // 错误
throw new Error('error')    // 正确
```
* **行末不留空格**。

* **不要使用 undefined 来初始化变量**。

```js
let name = undefined    // 错误
 
let name
name = 'value'          // 正确
```
* **循环语句中注意更新循环变量**。

```js
for (let i = 0; i < items.length; j++) {...}    // 错误
for (let i = 0; i < items.length; i++) {...}    // 正确
```
* **如果有更好的实现，尽量不要使用三元表达式**。

```js
let score = val ? val : 0     // 错误
let score = val || 0          // 正确
```
* **return，throw，continue 和 break 后不要再跟代码**。

```js
function doSomething () {
  return true
  console.log('never called')     // 错误
}
```
* **finally 代码块中不要再改变程序执行流程**。

```js
try {
  // ...
} catch (e) {
  // ...
} finally {
  return 42     // 错误
}
```
* **关系运算符的左值不要做取反操作**。

```js
if (!key in obj) {}       // 错误
```
* **避免不必要的 .call() 和 .apply()**。

```js
sum.call(null, 1, 2, 3)   // 错误
```
* **避免使用不必要的计算值作对象属性**。

```js
const user = { ['name']: 'John Doe' }   // 错误
const user = { name: 'John Doe' }       // 正确
```
* **禁止多余的构造器**。

```js
class Car {
  constructor () {      // 错误
  }
}
```

* **禁止不必要的转义**。
```js
let message = 'Hell\o'  // 错误
```
* **import, export 和解构操作中，禁止赋值到同名变量**。

```js
import { config as config } from './config'     // 错误
import { config } from './config'               // 正确
```
* **属性前面不要加空格**。

```js
user .name      // 错误
user.name       // 正确
```
* **禁止使用 with**。

```js
with (val) {...}    // 错误
```
* **对象属性换行时注意统一代码风格**。

```js
const user = {
  name: 'Jane Doe', age: 30,
  username: 'jdoe86'            // 错误
}
 
const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' }    // 正确
 
const user = {
  name: 'Jane Doe',
  age: 30,
  username: 'jdoe86'
}  
```
* **代码块中避免多余留白**。

```js
if (user) {
                            // 错误
  const name = getName()
 
}
 
if (user) {
  const name = getName()    // 正确
}
```
* **展开运算符与它的表达式间不要留空白**。

```js
fn(... args)    // 错误
fn(...args)     // 正确
```
* **遇到分号时空格要后留前不留**。

```js
for (let i = 0 ;i < items.length ;i++) {...}    // 错误
for (let i = 0; i < items.length; i++) {...}    // 正确
```
* **代码块首尾留空格**。
```js
if (admin){...}     // 错误
if (admin) {...}    // 正确
```

* **圆括号间不留空格**。
```js
getName( name )     // 错误
getName(name)       // 正确
```

* **一元运算符后面跟一个空格**。
```js
typeof!admin        // 错误
typeof !admin        // 正确
```

* **注释首尾留空格**。
```js
//comment           // 错误
// comment          // 正确
 
/*comment*/         // 错误
/* comment */       // 正确
```

* **模板字符串中变量前后不加空格**。
```js
const message = `Hello, ${ name }`    // 错误
const message = `Hello, ${name}`      // 正确
```

* **检查 NaN 的正确姿势是使用 isNaN()**。
```js
if (price === NaN) { }      // 错误
if (isNaN(price)) { }       // 正确
```

* **用合法的字符串跟 typeof 进行比较操作**。
```js
typeof name === 'undefimed'     // 错误
typeof name === 'undefined'     // 正确
```

* **自调用匿名函数 (IIFEs) 使用括号包裹**。
```js
const getName = function () { }()     // 错误
 
const getName = (function () { }())   // 正确
const getName = (function () { })()   // 正确
```

* **yield * 中的 * 前后都要有空格**。
```js
yield* increment()    // 错误
yield * increment()   // 正确
```

* **请书写优雅的条件语句（avoid Yoda conditions）**。
```js
if (42 === age) { }    // 错误
if (age === 42) { }    // 正确
```

#### 关于分号
* **不要使用分号**。
```js
window.alert('hi')   // 正确
window.alert('hi');  // 错误
```

* **不要使用 (, [, or ` 等作为一行的开始。在没有分号的情况下代码压缩后会导致报错，而坚持这一规范则可避免出错**。
```js
// 正确
;(function () {
  window.alert('ok')
}())
 
// 错误
(function () {
  window.alert('ok')
}())
```

```js
// 正确
;[1, 2, 3].forEach(bar)
 
// 错误
[1, 2, 3].forEach(bar)
```

```js
// 正确
;`hello`.indexOf('o')
 
// 错误
`hello`.indexOf('o')
```
> 相比更加可读易懂的代码，那些看似投巧的写法是不可取的。


* **比如**。
```js
;[1, 2, 3].forEach(bar)
```
建议的写法是
```js
var nums = [1, 2, 3]
nums.forEach(bar)
```
