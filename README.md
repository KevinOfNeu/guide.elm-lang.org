# 介绍

## 1. 介绍

**Elm 是一门编译成** `JavaScript` **的函数式编程语言。** Elm 被用来创建网页应用，与 `React` 类似。 Elm 强调简单，易用，工具链强大。

本指南包含如下内容：

* Elm 编程语言的基础
* 如何用 `Elm 架构` 建构交互式的应用
* 强调 Elm 这种与语言无关强大的架构模式

希望在指南结束后，你不仅能够用 Elm 创建网页应用，也能领悟到 Elm 的核心思想和设计模式。

如果你还在犹豫不决，我可以保证，只要你尝试一下 Elm，就可以写出更好的 `JavaScript` 以及 `React` 代码。

## 迅速上手

Elm 非常棒！ 这里有一个[计数器](http://elm-lang.org/examples/buttons)的例子。该案例的主要功能是做计数器做加减。

```text
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)

main =
  Html.beginnerProgram { model = 0, view = view, update = update }

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1

view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

_注_：`update` 和 `view` 完全解耦。你可以用声明的方式描述 HTML 的内容，Elm 负责处理 DOM。

## 为什么是一门函数式的语言？

忘记你所知道的关于函数式编程的一切吧。时尚的词汇，诡异的概念，糟糕的工具链，令人作吐。（_译者注_：这里并不一定是贬义词，无意冒犯） Elm 不一样：

* 无运行时错误。没有 `null`，`undefined` 
* 友好的错误提示，帮你更快的写 `feature`
* 随着代码量的增加，架构依然优秀
* 强制对 Elm package 进行语义化版本管理

没有任何的 JS 库的组合可以给予你这些特性，然而这些在 Elm 中都是自带的。Elm 之所以如此强大是因为 Elm 构建在 40+ 年的带类型函数式编程语言的工作基础上。因此，Elm 是一门函数式的编程语言，你花费几个小时阅读这份文档对你的实践非常有帮助。

我已经非常尽力的让 Elm 更加容易学习和使用，请给 Elm 一次机会吧，然后再回头想想这番话。我希望你也能被 Elm 惊艳到。

