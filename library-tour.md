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

