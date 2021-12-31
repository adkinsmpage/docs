# APIs For Plugins

我们开放了 API ，供 AdonS/Easier 或 Plugins 使用。

## COMMANDS

原生自带的 Command 通过 JavaScript Switch/Case + [dom-terminal](//npmjs.com/package/dom-terminal) 实现，但这明显不利于扩展已有命令。

因此我们在 `default` case 下将原有直接返回未找到信息改为了判断全局 `COMMANDS` 对象下是否存在相应属性，不存在才返回未找到。

因此如果自定义 Command ，可以通过修改全局 `COMMANDS` 对象来达到 增/删 的目的。

`COMMANDS` 对象的属性名会作为命令名，也就是用户键入的命令的第一个字符串。每个属性对应一个函数，调用此函数时会传入 `cmd, args` 两个属性，分别对应命令名和命令参数。

其中命令参数是一个数组。例如 当用户输入了 `hw string` 时，传入的 `cmd` 参数为 `"hw"`,`args` 参数为 `["string"]` 。

当需要在终端中回显某**字符串**时，需要使用 JavaScript 中的 `return` 语句。这里强调 JavaScript ，是想告诉您这个语句并不是 AdonS 定义/更改的而是 JavaScript 标准的内容。

例如 `return "xxx"` ，会在终端的新行中显示 "xxx" 。

如下 Demo ：

```js
COMMANDS.hw = function(cmd, args) {
  if (cmd == "hw") {
    if (args[0] == "string") {
      return "hw 命令正常"
    }
  }
}
```

!> 因为 `COMMANDS` 是个对象，很难保证您的属性不被其他 Plugin 占用，如果不加以检查就直接设置，可能会造成其他插件的命令被覆盖。

因此您在设置前应该检查您的目标属性是否等于 `undefined` (不要忘记使用严格等于或严格不等于运算符)。因此，上面的 Demo 应该改为这样：

```js
if (COMMANDS.hw !== undefined) { // 切记严格比较！
  COMMANDS.hw = function(cmd, args) {
    if (cmd == "hw") {
      if (args[0] == "string") {
        return "hw 命令正常"
      }
    }
  }
}
```

## methods

这可能是您未来比较常用的方法集，它封装了**亿**些有用的 API 。

| 方法调用            | 意义和用法                        | 调用方式、传入参数类型                                       |
| ---------- | ----------------------------------------------------- | ----------- |
| hideElementByFade | 用 FadeOut 动画隐藏某元素，需传入一个合法的 css 选择器字符串 | methods.hideElementByFade(cssQueryText: string) |
| showElementByFade | 与 hideElementByFade相反，用法相同 | methods.showElementByFade(cssQueryText: string) |
| formatDate | 给日期/时间补零，需传入一个时间字符串，例如 "4:3" "4/2" | methods.formatDate(dateOrTime: string) |
| import | Promise 新建 css/js 引用至 html，传入文件链接和类型 | methods.import(url: string, type: "css" \| "js") |
| throwError | 用系统提示框显示 Error，需传入字符串 | methods.throwError(errorText: string) |
| displayMsg | 显示一条消息，传入一个字符串 | methods.displayMsg(str: string) |

其中 `import` 支持 Promise 链式调用，返回的 Promise 解决为一个 HTMLLinkElement | HTMLScriptElement 类型的对象.

## store

其为 [Electron-store](//npmjs.org/package/electron-store/) 渲染器进程的对象引用，详见其 npm/github readme。

## pxmu

其为 [pxmujs](//pxmu.com) 的对象引用，详见官网。

## showPop

打开 pop 级页面，传入 pop div 的 id （: string）.

## closePop

与 `showPop` 相对，但无须传入字符串，而是传入字符串去掉引号的结果。例如打开 一个 id 为 `popDemo` 的 pop，打开时传入 `"popDemo"`, 关闭时传入 `popDemo` .
