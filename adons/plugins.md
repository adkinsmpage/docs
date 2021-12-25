# Plugin 开发

AdonS 的 Plugin 开发是极为简单的。它要求您有中等（甚至初级）的 JavaScript 技能。如果您能熟练操作 DOM/Naive Node.js ，那更好不过.

依靠 Electron 这一成熟框架，AdonS 能够同时使用 Chromium 提供的强大 Web API 和 Node 提供的强大 Naive API.

我们将底层的最高权限开放给 Plugin .只要是 JavaScript 能做到的，您都能用 Plugin 实现。

## 编写 JavaScript

AdonS Plugin Engine 对 您的代码复杂度极其危险性不做任何审查，这意味着您可以用它做任何事（甚至于用用户的资源去挖币）.

例如下面一个简单的 JavaScript 程序：

```js
window.close()
```

它将会是用户的噩梦：一打开 Easier ，一旦主程序加载完成，Easier 就会瞬间退出。

即使是这样的如此危险的 Plugin ，我们也不会对其审查。

然后，将您的 JS 文件上传到您的服务器或 GitHub/Gitee/GitLab/... 等空间，开始下一步吧！

## 编写 JSON

您作为一名 JavaScript ~~准~~程序员，应该用过 JSON 。在 AdonS Plugin Engine 中，他作为一个 Plugin 的安装分发包存在。下面是我们推荐的 JSON格式（也是我们 HelloWorld 程序的 JSON）:

```json
{
  "name": "HelloWorld",
  "version": "0.0.0",
  "description": "A Plugin Demo For AdonS",
  "main": "https://uazira.github.io/AdonS/Plugin/Plugin-SDK.js"
}
```

其中，没有任何属性是必须的，但您至少应该包含 `main` 属性。它规定了 Plugin 的主文件地址（即上面您上传到您的空间的地址，如果是 GitHub/GitLab/Gitee ，可以用他们提供的 Pages 服务。如果对 GitHub Pages 速度不满意，可以使用 Vercel 或 JSDelivr 进行加速），它应该能在公网被访问。

如果没有它，那么此 JSON 文件对于 AdonS Plugin Engine 来说是无效的。

其他的选项都很语义化：name 对应 Plugin 名，version 对应版本，description 对应P lugin 的介绍（它应该在十字以内，原因请看 [提交 Plugin 到 Plugin Store](#提交)）

需要注意的， name 属性需要使用 大驼峰式命名法，例如 `HelloWorld` `PlanRun` `CustomStyleJs` `CrackAdonS` 。 如不使用此命名，Plugin 会出现离奇 Bug.

## 提交

当您做好 JSON 文件时，就意味着您的 Plugin 做好了。接下来，测试一下：您的 Plugin JS 地址能否在浏览器访问？JSON 文件在 AdonS 中能否安装？

如果您这几个问题的答案都是“是”，那么，是时候把 Plugin 提交到 Store 了。 

进入我们的 [AdonS Awesome](https://github.com/Uazira/AdonS-Plugins), 编辑 `plugins.csv` 文件，在 GitHub 自动新建的行中写入如下信息:

```
<插件名>, <插件 json 地址>, <十字以内简介>
```

将尖括号内的信息替换，提交 Commit/PR ， 等待我们的审核，一旦通过，恭喜您，您的 Plugin 上架 Store 了！
