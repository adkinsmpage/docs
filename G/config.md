# 更多配置

首先，复制 `站点根目录/themes/g` 文件夹（下称主题配置文件）中的 `config.yml` 到 `站点根目录`，,重命名为`config.g.yml`。可以先复制到别的文件夹，重命名后再剪切到根目录。

这个文件我们暂且称之为 `主题根目录文件`，如果这个文件修改后不起效用，那就只能修改主题文件夹里的配置文件了 。

## Global

Global配置中主要是背景。之所以设置模糊度和色调强度，是因为在浏览器中，图片会稍微显得暗一点，而且由于本主题较多的透明效果，会导致图片喧宾夺主，这才特意加上这两个配置。

其他的基本不用说了。

## Links

Links同样采用Fluid设置方案，但CSS采用G的。

若需使用Links页面，您需要新建一个名为"links"的页面，并在其FrontMatter中添加如下内容：

```yaml
layout: links
```

## 404 & Categories & Tags

这三个页面采用自动部署，您只需决定加不加载。一旦选择加载，它将在Hexo Generate 之前编译。

如果您没有用于生成的插件，请安装。

```bash
# hexo-generator-category:
npm install hexo-generator-category

# hexo-generator-tag
npm install hexo-generator-tag
```