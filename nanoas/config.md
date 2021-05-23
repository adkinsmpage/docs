# 更多配置

首先，复制 `站点根目录/themes/nanoas` 文件夹（下称主题配置文件）中的 `config.yml` 到 `站点根目录/source/_data/`，如果没有这个目录，请新建。（在目前的Hexo版本中，应该是都没有的）

这个文件我们暂且称之为 `主题数据文件`。

## 页面顶部 Nav

你可以在数据文件中看到，有一项是“顶部Nav”，照着我填写的实例填写即可。

## DarkMode

有些用户向我反馈，说开启黑暗模式就会导致样式失常，这主要是由于我在开始的版本中没有加入开关，而本主题的黑暗模式并非采用一个CSS两套样式的方法，而是采用两个CSS切换，所以部署在子目录的用户就无法使用。在最新版本中我加入了开关，并默认关闭，部署在独立目录或Vercel、Netify的用户可以手动开启。

## Comments

本主题评论默认关闭，如需开启，在FrontMatter中设置：

```yaml
comments: true
```

即可开启评论功能。

评论是原作者写的，由于我没有账号，暂时没有测试过评论，如果评论出现Bug，不使用评论就可。

## Links

友链功能使用Fluid的配置方案和Butterfly的CSS，效果基本一致。

若需使用Links页面，您需要新建一个名为"links"的页面，并在其FrontMatter中添加如下内容：

```yaml
layout: links
```

## 404

本主题有一个 404 模板，与links相同，也也需要手动创建，但其的Front Matter需要这样设置：

```yaml
layout: 404
permalink: /404.html
```

## Tags & Categories

本主题不支持。