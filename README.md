# Dart 语言简明教程
**翻译自 Dart 官网，[查看原文](https://www.dartlang.org/guides/language/language-tour)。**

这篇文章展示如何使用 Dart 的各个主要特性，从变量和运算符到类和库，并且假定你已经会使用其他编程语言编写代码。
要详细了解 Dart 核心库相关内容，请看官方 [A Tour of the Dart Libraries](https://www.dartlang.org/guides/libraries/library-tour)。当你想对一个语言特性了解更多，无论何时都可以查阅官方 [Dart Language Specification](https://www.dartlang.org/guides/language/spec)。

> 小提示：在 DartPad 上，你可以尝试大部分 Dart 的语言特性（[了解更多](https://www.dartlang.org/tools/dartpad)）。
>
> 转到 [DartPatd](https://dartpad.dartlang.org/)

## 目录
* [一个基本的 Dart 程序](#一个基本的 Dart 程序)
* [重要概念](#重要概念)
* [关键字](#关键字)
* [变量](#变量)
  * [默认值](#默认值)
  * [Final 和 const](#Final-和-const)
* [内置类型](#内置类型)
  * [数值](#数值)
  * [字符串](#字符串)
  * [布尔](#布尔)
  * [Lists](#Lists)
  * [Maps](#Maps)
  * [Runes](#Runes)
  * [Symbols](#Symbols)
* [函数](#函数)
  * [可选参数](#可选参数)
  * [main() 函数](#main()-函数)
  * [函数作为一等对象](#函数作为一等对象)
  * [匿名函数](#匿名函数)
  * [作用域](#作用域)
  * [闭包](#闭包)
  * [测试函数的相等性](#测试函数的相等性)
  * [返回值](#返回值)
* [运算符](#运算符)
  * [算术运算符](#算术运算符)
  * [相等和相关运算符](#相等和相关运算符)
  * [类型测试运算符](#类型测试运算符)
  * [赋值运算符](#赋值运算符)
  * [逻辑运算符](#逻辑运算符)
  * [按位和移位运算符](#按位和移位运算符)
  * [条件运算符](#条件运算符)
  * [级联符号](#级联符号)
  * [其他运算符](#其他运算符)
* [控制流程语句](#控制流程语句)
  * [If 和 else](#If-和-else)
  * [For 循环](#For-循环)
  * [While 和 do-while](#While-和-do-while)
  * [Break 和 continue](#Break-和-continue)
  * [Switch 和 case](#Switch-和-case)
  * [Assert](#Assert)
* [异常](#异常)
  * [Throw](#Throw)
  * [Catch](#Catch)
  * [Finally](#Finally)
* [类](#类)
  * [使用类成员](#使用类成员)
  * [使用构造函数](#使用构造函数)
  * [获取对象类型](#获取对象类型)
  * [实例变量](#实例变量)
  * [构造函数](#构造函数)
  * [方法](#方法)
  * [抽象类](#抽象类)
  * [隐式接口](#隐式接口)
  * [扩展一个类](#扩展一个类)
  * [重写类成员](#重写类成员)
  * [可枚举类型](#可枚举类型)
  * [为一个类添加特新：混入](#为一个类添加特新：混入)
  * [类变量和方法](#类变量和方法)
* [泛型](#泛型)
  * [为什么用泛型？](#为什么用泛型？)
  * [使用集合字面量](#使用集合字面量)
  * [使用带构造函数的参数化类型](#使用带构造函数的参数化类型)
  * [泛型集合和它们包含的类型](#泛型集合和它们包含的类型)
  * [限制参数化类型](#限制参数化类型)
  * [使用泛型方法](#使用泛型方法)
* [库和可见性](#库和可见性)
  * [使用库](#使用库)
  * [实现库](#实现库)
* [异步支持](#异步支持)
  * [处理 Futures](#处理-Futures)
  * [声明异步函数](#声明异步函数)
  * [处理流](#处理流)
* [生成器](#生成器)
* [可调用的类](#可调用的类)
* [Isolates](#Isolates)
* [类型定义](#类型定义)
* [元数据](#元数据)
* [注释](#注释)
  * [单行注释](#单行注释)
  * [多行注释](#多行注释)
  * [文档注释](#文档注释)
* [总结](#总结)

## 一个基本的 Dart 程序
下面的代码使用了许多 Dart 的基本特性：
```Dart
// 定义函数
printInteger(int aNumber) {
  print('The number is $aNumber.'); // 打印到控制台
}

// 这里是程序开始执行的地方
main() {
  var number = 42; // 定义并初始化变量
  printInteger(number); // 调用函数
}
```
下面是这个程序使用的可适用于所有 (almost) Dart 应用的特性：

```Dart
// 这是一个单行注释
```
一个单行注释。Dart 也支持多行和文档注释。详情请看[注释](#)。

```dart
int
```
一个类型。其他的一些[基本类型](#)包括**字符串**、**List** 和**布尔**。

```Dart
42
```
一个数值字面量。数值字面量是一种编译期常量。

```Dart
print()
```
一种展示输出的方便方式。

```Dart
'...' (or "...")
```
一个字符串字面量。

```Dart
$variableName (or ${expression})
```
字符串插值：插入一个变量或者表达式的字符串值到一个字符串字面量里。详情请看[字符串](#)。

```Dart
main()
```
应用开始执行的特定的、必须的、顶级的函数。详情请看 [main() 函数](#)。

```Dart
var
```
一种声明变量但是不指定类型的方法。

> 注意：本篇文章的代码遵从 [Dart style guide](https://www.dartlang.org/guides/language/effective-dart/style) 中的公约。

## 重要概念
当你学习 Dart 语言的时候，请记住这些事实和概念：
* 所有可以放在一个变量里面的东西都是*对象*，而且所有对象都是*类*的实例。每一个数值、函数和 **null** 都是对象。所有的对象都继承自 [Object](#) 类。
* 尽管 Dart 是强类型的，但 Dart 可以推断类型所以类型声明是可选的。在上面的代码中，**number**被推断为类型  **int**。当你想要显式声明没有预期类型时，**使用特殊的 dynamic 类型**。
* Dart 支持泛型，像是 **List&lt;int&gt;**（包含整数的列表）或者 **List&lt;dynamic&gt;**（一个包含任意类型对象的列表）。
* 除了绑定在类和对象上的函数（分别为静态方法和实例方法）以外，Dart 还支持顶级函数（像是 **main()**)。你还可以在函数中创建函数（嵌套函数或局部函数）。
* 不像 Java，Dart 没有这些关键字：**pubilc**，**protected**，**private**。如果一个标识符以下划线 (\_) 开头，那么对于它的库来说是私有的。详情请看 [库和可见性](#)。
* 标识符可以以下划线 (\_) 开头，后见跟上任意字母和数字的组合。
* 有时候*表达式*和*语句*会有明显的区别，所以弄清楚它们的确切含义会很有帮助。
* Dart 相关工具会报告两种类型的问题：警告和错误。警告只是表明你的代码可能无法正常工作，但是并不会禁止你执行程序。错误可以是编译期或者运行期的。一个编译期错误完全禁止程序的执行；而运行期错误会在代码执行到这里时抛出一个[异常](#)。

## 关键字
下面的表格列出了 Dart 语言特殊对待的关键字。

| abstract <sup>1</sup> | do | import <sup>1</sup> | super |
| ------------ | ---- | ---- | ---- |
| as <sup>1</sup> | dynamic <sup>1</sup> | in | switch |
| assert | else | interface <sup>1</sup> | sync* <sup>2</sup> |
| async <sup>2</sup> | enum | is | this |
| async* <sup>2</sup> | export <sup>1</sup> | library <sup>1</sup> | throw |
| await <sup>2</sup> | external <sup>1</sup> | mixin <sup>1</sup> | true |
| break | extends | new | try |
| case | factory <sup>1</sup> | null | typedef <sup>1</sup> |
| catch | false | operator <sup>1</sup> | var |
| class | final | part <sup>1</sup> | void |
| const | finally | rethrow | while |
| continue | for | return | with |
| covariant <sup>1</sup> | get <sup>1</sup> | set <sup>1</sup> | yield <sup>2</sup> |
| default | if | static <sup>1</sup> | yield <sup>2</sup> |
| deferred <sup>1</sup> | implements <sup>1</sup> |      |      |

<sup>1</sup> 带角标1的单词为**内置标识符**。不要使用内置标识符作为标识符。如果你使用内置标识符作为类名或者类型名，会引发一个编译期错误。

<sup>2</sup> 带角标2的单词是新的，在 Dart 的1.0版本发布之后作为**异步**支持加入的有限保留词。在以 **async**、**async\*** 或 **yield** 标识的函数体中，你不能使用 **async**、**await** 或者 **yield** 作为标识符。详情请看[异步支持](#)。

关键词表里的其他所有单词都是**保留词**。你不能使用它们作为标识符。



## 变量

这里是创建并初始化一个变量的例子：

```Dart
var name = 'Bob';
```

变量保存的是引用。名字是 **name** 的变量包含一个指向值为 "Bob" 的**字符串**对象的引用。

名字为 **name** 的变量类型被推断为 **String**，但是你可以通过显示指定类型来改变这个行为。如果一个对象不限制为一个单一的类型，指定它为 **Object** 或 **dynamic** 类型。

```dart
dynamic name = 'Bob';
```

另一个选项是显式指定类型为它将会被推断的类型：

```dart
String name = 'Bob';
```

> 注意：对于局部变量，本篇文章遵守[代码风格推荐](https://www.dartlang.org/guides/language/effective-dart/design#types)使用 var，而不是类型声明。

### 默认值

未初始话的变量有一个初始值 **null**。即使是数值类型的变量初始值也是 null，因为数值——和 Dart 中其他所有类型一样——都是对象。

```dart
int lineCount;
assert(lineCount == null);
```

> 注意：代码中的**assert()**调用。在开发时，**assert(*condition*)** 会抛出一个异常，除非 *condition* 的结果是 true。详情请看 [Assert](#)。

### Final 和 const

如果你从不打算改变一个变量，使用 **final** 和 **const**，而不是 **var** 或者一个类型名。一个 final 变量只可以被设置一次；一个 const 变量是编译期常量。（Const 变量是显式 final 的。）一个 final 的顶级变量或者类变量在首次被使用时初始化。

> 注意：实例变量只可以是 final 的，不可以是 const 的。

这里是创建并设置一个 final 变量的例子：

```dart
final name = 'Bob'; // 没有类型声明
final String nickname = 'Boddy';
```

你不可以改变一个 final 变量的值：

```dart
name = 'Alice'; // 错误：一个final变量只可以被设置一次
```

对那些你想要作为**编译期常量**的变量使用 **const**。如果这个 const 变量是类级别的，使用 **static const** 标识它。在你声明的地方，设置变量的值为编译器常量比如数字或字符串字面量、另一个常量或者常量数值的算术运算结果。

```dart
const bar = 1000000; // 压力单位（达因/cm2）
const double atm = 1.01325 * bar; // 标准大气压
```

**Const** 关键字不仅可以声明常量。你还可以使用它创建常量值，也可以声明创建常量值的构造函数。任何变量都可以拥有一个常量值。

```dart
var foo = const [];
final bar = const [];
const baz = []; // 等同于 `const []`
```

你可以忽略常量声明中初始化表达式中的 **const**，像上面的 **baz** 一样。详情请看[不要重复使用 const](https://www.dartlang.org/guides/language/effective-dart/usage#dont-use-const-redundantly)。

你可以改变一个非 final 且非 const 变量的值，即使它有一个常量值。

```dart
foo = [1, 2, 3]; // 之前是 const []
```

你不可以改变一个常量的值：

```dart
baz = [42]; // 错误：常量不可以被赋值
```

要了解更多使用 **const** 创建常量值的内容，请看 [List](#)、[Map](#) 和[类](#)。

## 内置类型

Dart 语言对以下类型有特殊的支持：

* numbers（数值）
* strings（字符串）
* booleans（布尔）
* lists (也称为 *arrays*)
* maps
* runes (在字符串中表示一个Unicode字符)
* symbols

你可以使用字面量初始化以上任意类型。比如，**'this is a string'** 就是一个字符串字面量，而 **true** 是一个boolean字面量。

由于 Dart 中的所有变量都是对象的引用——一个类的实例——所有你通常可以使用*构造函数*来初始化变量。某些内置类型有它们自己的构造函数。比如，你可以使用 **Map()** 构造函数创建一个 map。

### 数值

Dart 中的数值有两种类型：

#### int

小于等于64位的整数值，实际长度依赖运行平台。在 Dart 虚拟机上，可以是 -2<sup>63</sup> 到 2<sup>63<sup> 次方 -1。编译到 JavaScript 的 Dart 使用[JavaScript的数值](https://stackoverflow.com/questions/2802957/number-of-bits-in-javascript-numbers/2803010#2803010)，允许从 -2<sup>53</sup> 到 2<sup>53</sup> - 1的值。

#### double

64位（双精度）浮点数值，如 IEE 754 标准中所规定的。

**Int** 和 **double** 都是 [num](https://api.dartlang.org/dev/dart-core/num-class.html) 的子类。Num 类型包含像 +，-，/ 和 * 这样的基本运算符，也是 **abs()**、**ceil()** 和 **floor()** 适用的类型。（像 &gt;&gt; 的位运算符定义在 int 类中。）如果你从 num 和它的子类中找不到你想要的，试着看看 [dart:math](https://api.dartlang.org/dev/dart-math) 库。

整数是没有小数点的数字。下面是一些定义整数字面量的例子：

```dart
int x = 1;
int hex = 0xDEADBEEF;
```

如果一个数字包含小数点，那么它是一个浮点数。下面是一些定义浮点数字面量的例子：

```dart
double y = 1.1;
double exponents = 1.42e5;
```

下面是一些数值和字符串互相转换的例子：

```dart
// String -> int
var one = int.parse('1');
assert(one == 1);

// String -> double
var onePointOne = double.parse('1.1');
assert(onePointOne == 1.1);

// int -> String
String oneAsString = 1.toString();
assert(oneSAsString == '1');

// double -> String
String piAsString = 3.14159.toStringAsFixed(2);
assert(piAsString == '3.14');
```

整数类型支持传统的位运算符，比如移位 (&lt;&lt;, &gt;&gt;) 、按位与 (&) 和按位或 (|)。下面是一个例子：

```dart
assert((3 << 1) == 6); // 0011 << 1 == 0110
assert((3 >> 1) == 1); // 0011 >> 1 == 0001
assert((3 | 4) == 7); // 0011 | 0100 == 0111
```

以字面量定义的数值是编译期常量。许多算术表达式也同样是编译器常量，只要它们的操作数是编译期常数且最后得到一个数值。

```dart
const msPerSecond = 1000;
const secondsUntilRetry = 5;
const msUntilRetry = secondsUntilRetry * msPerSecond;
```

### 字符串

Dart 的字符串是以 UTF-16 编码单元组成的序列。你可以使用单引号或者双引号来创建字符串：

```dart
var s1 = 'Single quotes work well for string literals.';
var s2 = "Double quotes work just as well.";
var s3 = 'It\'s easy to escape the string delimiter.';
var s4 = "It's even easier to use the other delimiter.";
```

你可以使用 **${*expression*}** 将一个表达式插入到字符串中。如果这个表达式是一个标识符，你可以省略 {}。为了得到一个对象的字符串表示，Dart 会调用对象的 **toString()** 方法。

```dart
var s = 'string interpolation';

assert('Dart has $s, which is very handy.' ==
    'Dart has string interpolation, ' +
        'which is very handy.');
assert('That deserves all caps. ' +
        '${s.toUpperCase()} is very handy!' ==
    'That deserves all caps. ' +
        'STRING INTERPOLATION is very handy!');
```

> 注意：== 运算符测试两个对象是否相等。两个字符串相等的条件是它们包含同样的编码单位序列

你可以通过并排字符串字面量或者使用 **+** 运算符来串联字符串：

```dart
var s1 = 'String '
    'concatenation'
    " works even over line breaks.";
assert(s1 ==
    'String concatenation works even over '
    'line breaks.');

var s2 = 'The + operator ' + 'works, as well.';
assert(s2 == 'The + operator works, as well.');
```

另一种方式是创建一个多行字符串：使用三个引号（单引号或双引号）来标记：

```dart
var s1 = '''
You can create
multi-line strings like this one.
''';

var s2 = """This is also a
multi-line string.""";
```

你可以通过 **r** 前缀来创建一个”原始的“字符串：

```dart
var s = r"In a raw string, even \n isn't special.";
```

要详细了解 Unicode 字符在字符串中是怎样表示的，请看 [Runes](#)。

只要所有插值表达式是编译期常量，可以计算出 null 或者 数值、字符串、布尔值，那么这个字面量的字符串就是编译期常量。

```dart
// 可作为常量字符串的组成部分
const aConstNum = 0;
const aConstBool = true;
const aConstString = 'a constant string';

// 不可作为常量字符串的组成部分
var aNum = 0;
var aBool = true;
var aString = 'a string';
const aConstList = [1, 2, 3];

const validConstString = '$aConstNum $aConstBool $aConstString';
// const invalidConstString = '$aNum $aBool $aString $aConstList';
```

要了解更多使用字符串的信息，请看 [字符串和正则表达式](#)。

