# 安装

> **注:** 如果你不想安装，可以使用[在线编辑器](http://elm-lang.org/try) 以及 [在线 REPL](http://elmrepl.cuberoot.in/)。

## 安装

* Mac — [安装](https://44a95588fe4cc47efd96-ec3c2a753a12d2be9f23ba16873acc23.ssl.cf2.rackcdn.com/Elm-Platform-0.18.pkg)
* Windows — [安装](https://44a95588fe4cc47efd96-ec3c2a753a12d2be9f23ba16873acc23.ssl.cf2.rackcdn.com/Elm-Platform-0.18.exe)
* Anywhere — [npm 安装](https://www.npmjs.com/package/elm) or [源码安装](https://github.com/elm-lang/elm-platform)

安装完毕后，下面的命令行工具可以使用:

* [`elm-repl`](install.md#elm-repl) — Elm REPL
* [`elm-reactor`](install.md#elm-reactor) — 提高项目开发速度（原文:get a project going quickly）
* [`elm-make`](install.md#elm-make) — 编译某个目录下的 Elm 代码
* [`elm-package`](install.md#elm-package) — 下载 package

在配置好编辑器后，我们再详细描述他们是怎么协同共工作的。

> **Troubleshooting:** 提高学习速度最快的方式是参与到 Elm 社区和他们交流。我们愿意沟通和提供帮助！如果你遇到什么问题，欢迎来 [Elm Slack](http://elmlang.herokuapp.com/) 提问。事实上，这样节省你自己的时间。不要犹豫！

### 配置编辑器

好的编辑器可以在你学习 Elm 过程中助你一臂之力。下面的编辑器中都有 Elm 的插件:

* [Atom](https://atom.io/packages/language-elm)
* [Brackets](https://github.com/lepinay/elm-brackets)
* [Emacs](https://github.com/jcollard/elm-mode)
* [IntelliJ](https://github.com/durkiewicz/elm-plugin)
* [Light Table](https://github.com/rundis/elm-light)
* [Sublime Text](https://packagecontrol.io/packages/Elm%20Language%20Support)
* [Vim](https://github.com/ElmCast/elm-vim)
* [VS Code](https://github.com/sbrink/vscode-elm)

如果上面的编辑器你都不喜欢，那么 [Sublime Text](https://www.sublimetext.com/) 是个不错的选择！

你可以试试 [elm-format](https://github.com/avh4/elm-format)，帮助你格式化代码。

### 命令行工具

安装完 Elm 后你或许好奇 `elm-repl`, `elm-reactor`, `elm-make`, 和 `elm-package` 命令具体都是做什么的?

#### elm-repl

[`elm-repl`](https://github.com/elm-lang/elm-repl) 让你做表达式求值\(译者注： Read, Evaluate, Print, Loop\)。

```bash
$ elm-repl
---- elm-repl 0.18.0 -----------------------------------------------------------
 :help for help, :exit to exit, more at <https://github.com/elm-lang/elm-repl>
--------------------------------------------------------------------------------
> 1 / 2
0.5 : Float
> List.length [1,2,3,4]
4 : Int
> String.reverse "stressed"
"desserts" : String
> :exit
$
```

我们将在 “语言核心概念” 章节使用 `elm-repl`，更多细节请阅读[这里](https://github.com/elm-lang/elm-repl/blob/master/README.md)。

> **注:** `elm-repl` 将代码编译成 JavaScript 后执行, 确保你安装了 [Node.js](http://nodejs.org/) 。

#### elm-reactor

[`elm-reactor`](https://github.com/elm-lang/elm-reactor) helps you build Elm projects without messing with the command-line too much. You just run it at the root of your project, like this:

[`elm-reactor`](https://github.com/elm-lang/elm-reactor) 帮你一句命令搞定整个工程。你只需要在项目的根目录下指定如下命令：

```bash
git clone https://github.com/evancz/elm-architecture-tutorial.git
cd elm-architecture-tutorial
elm-reactor
```

这句命令在 [`http://localhost:8000`](http://localhost:8000) 启动了一个服务。你可以浏览任何一个 Elm 文件，例如 `examples/01-button.elm`。

**值得注意的 flags:**

* `--port` 指定端口号. 比如

  `elm-reactor --port=8123` 指定服务运行在 `http://localhost:8123`。

* `--address` 可以替换默认的 `localhost` 成其他的地址. 比如使用 `elm-reactor --address=0.0.0.0` 让你的服务监听局域网所有的请求。

### elm-make

[`elm-make`](https://github.com/elm-lang/elm-make) 用来编译 Elm 工程成 HTML 或者 JavaScript。这是最常用的编译 Elm 代码的方式，如果你的代码无需用`elm-reactor`调试，可以直接运行 `elm-make` 来构建。

假设你要编译 `Main.elm` 成 HTML 文件 `main.html`，你需要执行：

```bash
elm-make Main.elm --output=main.html
```

**值得注意的 flags:**

* `--warn` 打印警告语句以提高代码质量

#### elm-package

[`elm-package`](https://github.com/elm-lang/elm-package) 用来下载和发布到[package catalog](http://package.elm-lang.org/)。作为社区成员解决问题[更好的办法](http://package.elm-lang.org/help/design-guidelines)，代码分享出来让大家使用才是王道！

假设你需要使用 [`elm-lang/http`](http://package.elm-lang.org/packages/elm-lang/http/latest) 和 [`NoRedInk/elm-decode-pipeline`](http://package.elm-lang.org/packages/NoRedInk/elm-decode-pipeline/latest) 来做网络请求，并且将返回的结果转换成 JSON，你可以这样做：

```bash
elm-package install elm-lang/http
elm-package install NoRedInk/elm-decode-pipeline
```

这句命令把依赖安装到 `elm-package.json` 文件。（`elm-package.json` 文件描述项目，如果没有的话，可以手动创建）,更多姿势请移步 [这里](https://github.com/elm-lang/elm-package)!

**值得关注的命令:**

* `install`: 安装依赖到项目，并修改描述文件 `elm-package.json`
* `publish`: 发布你的 Elm Package
* `bump`: 根据 API 改变来解决版本号之间的冲突
* `diff`: 查看两个 API 之间的区别

