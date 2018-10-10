# Dart 库教程

翻译自 Dart 官网，[查看原文](https://www.dartlang.org/guides/libraries/library-tour)。

当前版本：2.0.0 (stable)

完成度：1%

该教程为你展示了下面这些库的主要特性，这些库被包含在所有的 Dart 平台中。

[dart:core](#)

内置类型、集合和其他核心功能。该库在每一个 Dart 程序中被自动引入。

[dart:async](#)

支持异步编程，包括 Future 和 Stream 等类。

[dart:math](#)

数学常数和函数，外加随机生成器。

[dart:convert](#)

用于在不同的数据表示之间进行转换的编码器和解码器，包括 JSON 和 UTF-8。

该篇文章只是一个概览；它只覆盖 dart:* 中的一小部分库而且不包含第三方库。平台相关的 dart:io 和 dart:html 库分别包含在 [dart:io 教程](#) 和 [dart:html 教程](#) 中。

其他查找库信息的地方是 [pub.dartlang.org](#) 和 [Dart web 开发者库指引](#)。 你可以在 [Dart API 参考](#) 中找到所有的 dart:* 库；而如果你在使用 Flutter，则是 [Flutter API 参考](#)。

> DartPad 小提示：你可以通过将其拷贝到 [DartPad](#) 来尝试本页的代码。

## dart:core —— 数值、集合、字符串和其他

库 dart:core（[API 参考](#)）提供了一组小而重要的内置功能。这个库在所有的 Dart 程序中被自动引入。

### 打印到控制台

顶级方法 **print()** 接受单个参数（任意类型）并将这个对象的字符串值（通过 **toString()** 返回）显示在控制台上。

```dart
print(anObject);
print('I drink $tea.');
```

要了解更多关于基本的字符串和 **toString()** 的信息，请参阅语言教程中的 [String](#) 章节。

### 数值

库 dart:core 定义了 num、int 和 double 类，它们拥有操作数值的一些基本方法。

你可以通过 int 和 double 的 **parse()** 方法将字符串分别转换为整数或浮点数：

```dart
assert(int.parse('42') == 42);
assert(int.parse('0x42') == 66);
assert(double.parse('0.50') == 0.5);
```

或者使用 num 的 parse() 方法，它在可能的情况下创建一个整数，否则创建一个浮点数：

```dart
assert(num.parse('42') is int);
assert(num.parse('0x42') is int);
assert(num.parse('0.50') is double);
```

要指定一个整数的进制，添加 **radix** 参数：

```dart
assert(int.parse('42', radix: 16) == 66);
```

使用 **toString()** 方法将一个 int 或者 double 装换成字符串。要指定小数点右边的位数，请使用 [toStringAsFixed()](#)。要指定字符串中的有效位数，请使用 [toStringAsPrecision()](#) ：

```dart
// 转换 int 为字符串
assert(42.toString() == '42');

// 转换 double 为字符串
assert(123.456.toString() == '123.456');

// 指定小数点后的位数
assert(123.456.toStringAsFixed(2) == '123.46');

// 指定数值的有效位数
assert(123.456.toStringAsPrecision(2) == '1.2e+2');
assert(double.parse('1.2e+2') == 120.0);
```

要了解更多信息，请参阅 [int](#)、[double](#) 和 [num](#) 的 API 文档。也请参阅 [dart:math](#) 章节。

### 字符串和正则表达式

字符串在 Dart 中表示 UTF-16 编码单元组成的一个不可变序列。语言教程中有关于 [字符串](#) 的更详细信息。你可以使用正则表达式（RegExp 对象）在字符串中查找和替换部分字符串。

字符串类定义了诸如 **split()**、**contains()**、**startsWith()**、**endsWith** 这样的以及其他更多的方法。

#### 在字符串中查找

你可以在字符串中查找一个指定模式的位置，或者检查字符串是否以其开头或结尾。比如：

```dart
// 检查一个字符串是否包含另一个字符串
assert('Never odd or even'.contains('odd'));

// 检查一个字符串是否开始于另一个字符串
assert('Never odd or even'.startsWith('Never'));

// 检查一个字符串是否结束于另一个字符串
assert('Never odd or even'.endsWith('even'));

// 查找一个字符串在另一个字符串中的位置
assert('Never odd or even'.indexOf('odd') == 6);
```

#### 从字符串中提取数据

你可以从一个字符串中获取独立的字符分别作为字符串或者整数。准确来说，你得到的其实是独立的 UTF-16 编码单元；像高音音符这样的高位字符 (‘\u{1D11E}’) 为在一块的两个编码单元。

你也可以提取一个子字符串或者拆分一个字符串为一个子字符串列表：

```dart
// 抓取一个子字符串
assert('Never odd or even'.substring(6, 9) == 'odd');

// 使用一个字符串模式拆分字符串
var parts = 'structured web apps'.split(' ');
assert(parts.length == 3);
assert(parts[0] == 'structured');

// 使用索引获取 UTF-16 编码单元（作为字符串）
assert('Never odd or even'[0] == 'N');

// 使用空字符串作为 split() 的参数来获得
// 所有字符（作为字符串）的列表；便于迭代
for (var char in 'hello'.split('')) {
  print(char);
}

// 获取字符串中所有的 UTF-16 编码单元
var codeUnitList =
    'Never odd or even'.codeUnits.toList();
assert(codeUnitList[0] == 78);
```

#### 大小写转换

你可以很容易地转换一个字符串为它的大写或小写形式：

```dart
// 转换为大写
assert('structured web apps'.toUpperCase() ==
    'STRUCTURED WEB APPS');

// 转换为小写
assert('STRUCTURED WEB APPS'.toLowerCase() ==dart
    'structured web apps');
```

> 说明：这些方法并不适用于所有语言。比如，土耳其字母的 *I* 转换就是错误的。

#### 修剪和空字符串

使用 **trim()** 移除前面和后面的所有空白。要检查一个字符串是否是空的（长度为0），使用 **isEmpty**。

```dart
// 修剪字符串
assert('  hello  '.trim() == 'hello');

// 检查字符串是否是空的
assert(''.isEmpty);

// 只有空白符的字符串不是空的
assert('  '.isNotEmpty);
```

#### 替换字符串的部分内容

字符串是不可变的对象，意味着你可以创建它们但是不可以修改它们。如果你仔细观察 [String API 索引](#)，你会发现没有一个方法真正改变了一个字符串的状态。比如，方法 **replaceAll()** 不会修改原来的字符串：

```dart
var greetingTemplate = 'Hello, NAME!';
var greeting =
    greetingTemplate.replaceAll(RegExp('NAME'), 'Bob');

// greetingTemplate 没有改变
assert(greeting != greetingTemplate);
```

#### 构建一个字符

要程序化的创建一个字符串，你可以使用 StringBuffer。一个 StringBuffer 不生成新的字符串除非 **toString()** 方法被调用。方法 **writeAll()** 有一个可选的第二个参数让你可以指定一个分隔符——在这里是一个空格。

```dart
var sb = StringBuffer();
sb
  ..write('Use a StringBuffer for ')
  ..writeAll(['efficient', 'string', 'creation'], ' ')
  ..write('.');

var fullString = sb.toString();

assert(fullString ==
    'Use a StringBuffer for efficient string creation.');
```

#### 正则表达式

RegExp 类提供了与 JavaScript 中正则表达式相同的功能。使用正则表达式来高效地查找和匹配字符串中的模式。

```dart
// 这是一个表示一个或多个数字的正则表达式
var numbers = RegExp(r'\d+');

var allCharacters = 'llamas live fifteen to twenty years';
var someDigits = 'llamas live 15 to 20 years';

// contains() 可以使用正则表达式
assert(!allCharacters.contains(numbers));
assert(someDigits.contains(numbers));

// 替换所有匹配的部分为另一个字符串
var exedOut = someDigits.replaceAll(numbers, 'XX');
assert(exedOut == 'llamas live XX to XX years');
```

你也可以直接使用 RegExp 类。Match 类提供了对于正则表达式匹配结果的访问方法。

```dart
var numbers = RegExp(r'\d+');
var someDigits = 'llamas live 15 to 20 years';

// 检查正则表达式在字符串中是否有一个匹配
assert(numbers.hasMatch(someDigits));

// 循环遍历所有匹配结果
for (var match in numbers.allMatches(someDigits)) {
  print(match.group(0)); // 15，然后是 20
}
```

#### 更多信息

参考 [String API 索引](#) 来获取方法的完整列表。另请参阅 [StringBuffer](#)、[Pattern](#)、[RegExp](#) 和 [Match](#) 的 API 索引。