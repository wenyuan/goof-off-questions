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

**15）对象（伪数组）调用 `push` 方法，输出结果是什么？**

```javascript
var obj = {
  '2': 3,
  '3': 4,
  'length': 2,
  'splice': Array.prototype.slice,
  'push': Array.prototype.push
}
obj.push(1)
obj.push(2)
console.log(obj)

// 输出结果
// [empty × 2, 1, 2, splice: ƒ, push: ƒ]
```

知识点（[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/push）)）：
- 具有数字索引且带有 `length` 属性的对象又被称为类数组。
- `push` 方法可向数组的末尾添加一个或多个元素，并返回新的长度。注：该方法会改变数组的长度。
  - `push` 方法具有通用性。该方法和 `call` 或者 `apply` 一起使用时，可应用在类数组对象上。
  - `push` 方法根据 `length` 属性来决定从哪里开始插入给定的值。
  - 如果 `length` 属性不能被转成数值，则执行 `push` 方法时插入的元素索引位置为 `0`。
  - 如果 `length` 属性不存在，则执行 `push` 方法时会自动创建它。
- 当对象带有数组的 `splice` 方法并且 `length` 属性的值可以转为数值时，对象将会被当做数组打印。

解析：
- 这个 `obj` 中定义了两个 key 值，分别为 `splice` 和 `push`，分别对应数组原型中的 `splice` 和 `push` 方法，因此这个 `obj` 可以调用数组中的 `push` 和 `splice` 方法。
- 调用对象的 `push` 方法：`obj.push(1)`，因为此时 `obj` 中 `{ length: 2 }`，所以从索引为 `2` 的位置开始插入，也就是数组的第三项。因为数组索引是从 `0` 开始的，这时已定义了索引 `2` 和 `3` 的两项 `{ '2': 3, '3': 4 }`，所以 `obj.push(1)` 会替换下标为 `2` 的一项，此时 `{ length: 3}` ；`obj.push(2)` 会替换掉索引下标为 `3` 的一项，此时 `{ length: 4 }` 。
- 此时索引 `2` 和 `3` 的两项为 `{ '2': 1, '3': 2 }` 。输出结果就是：`Object(4) [empty × 2, 1, 2, splice: ƒ, push: ƒ]`。因为只是定义了 `2` 和 `3` 两项，没有定义`0` 和 `1` 两项，所以前面两项是 `empty`。
