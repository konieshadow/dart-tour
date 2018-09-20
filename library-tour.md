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