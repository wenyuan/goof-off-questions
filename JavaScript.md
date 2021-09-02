## JavaScript

**01）for...of for...in 为什么可以遍历字符串和对象**

**02）promise async源码**

**03）promise  catch和失败的回调有什么区别**

**04）正则replace的第二个参数的用法**

**05）宏微任务，微任务常用的那些**

**06）setTimeout的wait参数传入0会即可执行吗**

**07）setTimeout其它参数**

**08）关于wait能再说说吗**

**09）`console.log([1,2,3,4][1,2]);` 这个输出啥，为啥**

**10）`console.log('1'- - '1');` 输出啥**

- 输出 `2`。
- 题中相同的符号表征了两个不同的运算符：负号运算符，即反转符号的一元运算符，减法运算符，是从另一个数减去一个数的二元运算符。
- 一元负号执行优先级高于减号。
- 二元运算符参与计算时，对于 `+`，从字符串类型的运算元开始，它 将合并（连接）各个字符串。其他算术运算符只对数字起作用，并且总是将其运算元转换为数字。
- 参考[基础运算符，数学](https://zh.javascript.info/operators)。

**11）原型继承除了 `Object.crate`，还有啥**

**12）输出什么（变量提升问题）**

- 输出 `4`

```javascript
var getName = function () { console.log (4);};
function getName() { console.log(5); }
  
let ret = getName();
console.log(ret);
  
// 解析
// 在初始化阶段，function getName() { console.log(5); }  var getName;
// 在执行阶段，getName 被重新赋值为 function () { console.log (4);};
// 执行 getName();
```

**13）CommonJS 中的 require/exports 和 ES6 中的 import/export 区别？**

**14）babel的实现原理和具体过程是什么？**
