# Hexo

- [ ] 生成每日格言

# 常见指令

| 指令                       | 用途                                                         |
| -------------------------- | ------------------------------------------------------------ |
| hexo init                  | 在当前目录下创建工程                                         |
| _config.yml                | deploy:   type: git   repository: git@github.com:liuxianan/liuxianan.github.io.git   branch: master |
| hexo clean                 | 清除缓存                                                     |
| hexo g                     | 生成web                                                      |
| hexo s                     | 启动web服务并预览，在浏览器输入 <http://localhost:4000>      |
| hexo d                     | 发布pulic 目录下的静态页面至github                           |
| git clone url themes/yilia | 下载指定主题到根目录/thems/yilia/ 下                         |
| hexo new "postName"        | 新建文章，hexo n                                             |
| hexo new page "pageName"   | #新建页面                                                    |
| hexo generate              | 生成静态页面至public目录，hexo g                             |
| hexo server                | 开启预览访问端口（默认端口4000，'ctrl + c'关闭server）       |
| hexo deploy                | hexo d                                                       |
| hexo s -g                  | 生成并本地预览                                               |

# 常用插件

| <div style="width: 50%">名称   </div>                | <div style="width: 50%"> 用途   </div> |
| ---------------------------------------------------- | -------------------------------------- |
| [hexo-douban](https://gitee.com/mirrors/hexo-douban) | 生成豆瓣数据                           |
| hexo-toc                                             | 文档插件显示二级目录，响应点击事件     |
| hexo-renderer-markdown-it-plus                       | markdown解析插件                       |
| hexo-reference                                       | 自动生成wiki索引                       |
| hexo-valkyr-url                                      | 自动根据url生成卡片                    |

# 插入每日格言

参考1[关于给hexo博客增加每日一言（诗句，影视名句，网易云热评等） - 灰信网（软件开发博客聚合） (freesion.com)](https://www.freesion.com/article/32621419855/)

参考2[hexo(next)——每日一言、今日诗词_cloudYun的博客-CSDN博客](https://blog.csdn.net/qq_44036990/article/details/105088198)

# 支持流程图
参考这个[链接](http://mermaid-js.github.io/mermaid/#/integrations?id=blogs)
我的网站使用的是该链接下的这个[插件](https://github.com/webappdevelp/hexo-filter-mermaid-diagrams)
第一步安装：`$ yarn add hexo-filter-mermaid-diagrams`
第二步配置：
```java
# mermaid chart
mermaid: ## mermaid url https://github.com/knsv/mermaid
  enable: true  # default true
  version: "7.1.2" # default v7.1.2
  options:  # find more api options from https://github.com/knsv/mermaid/blob/master/src/mermaidAPI.js
    #startOnload: true  // default true
```
第三步插入：
在after_footer.pug插入
```java
if theme.mermaid.enable == true
  script(type='text/javascript', id='maid-script' mermaidoptioins=theme.mermaid.options src='https://unpkg.com/mermaid@'+ theme.mermaid.version + '/dist/mermaid.min.js' + '?v=' + theme.version)
  script.
    if (window.mermaid) {
      var options = JSON.parse(document.getElementById('maid-script').getAttribute('mermaidoptioins'));
      mermaid.initialize(options);
    }

```
在after-footer.ejs插入
```java
<% if (theme.mermaid.enable) { %>
  <script src='https://unpkg.com/mermaid@<%= theme.mermaid.version %>/dist/mermaid.min.js'></script>
  <script>
    if (window.mermaid) {
      mermaid.initialize({theme: 'forest'});
    }
  </script>
<% } %>

```
# 支持数学公式显示

默认使用next主题
在主题配置文件配置如下：
```shell
# MathJax Support
mathjax:
  enable: true
  per_page: true
  cdn: //cdn.bootcss.com/mathjax/2.7.1/latest.js?config=TeX-AMS-MML_HTMLorMML
```
在每篇文章头配置如下：
```shell
title: index.html
date: 2016-12-28 21:01:30
tags:
mathjax: true

```

# 生成论文式索引

**安装插件**

```shell
npm install hexo-reference --save
```

**用法**

```js
basic footnote[^1]
here is an inline footnote[^2](inline footnote)
and another one[^3]
and another one[^4]

[^1]: basic footnote content
[^3]: paragraph
footnote
content
[^4]: footnote content with some [markdown](https://en.wikipedia.org/wiki/Markdown)
```

**效果图**

![mark](http://cdn.yangchaofan.cn/BlogGifRes/20210314/Cqc6Simj6jvS.png?imageslim)

# 生成链接卡片

[**安装插件**](https://github.com/toastsgithub/hexo-valkyr-url)

```shell
npm install hexo-valkyr-url
```

用法

```js
{% valkyrurl [url=http://example.com][otherOpt=value] %}
```

**典型实例**

```js
<% valkyrurl
[url=http://mindhacks.cn/2009/02/15/why-you-should-start-blogging-now]
[title="为什么你应该（从现在开始就）写博客"]
[avatar=http://mindhacks.cn/wp-content/uploads/2009/02/reussirsonblog.jpg]
[desc="blogging now"]
%>
```



效果如下：![mark](http://cdn.yangchaofan.cn/BlogGifRes/20210314/VIuteghykuse.png?imageslim)



# 配置鼠标样式

`themes\leaf\source\css\_custom\custom.styl`路径下配置curso游标图片

```js


/*鼠标样式*/
* {
  cursor: url(http://cdn.yangchaofan.cn/BlogGifRes/20210322/Ktdi8ORPSLgx.cur),auto;
}
:active {
  cursor: url(http://cdn.yangchaofan.cn/BlogGifRes/20210322/jXa2I1K2HCIO.cur),auto
}
:link {
  cursor: url(http://cdn.yangchaofan.cn/BlogGifRes/20210322/jXa2I1K2HCIO.cur),auto
}
```



# 生成b站卡片

[**安装插件**](https://github.com/MaxChang3/hexo-bilibili-card)

```shell
npm install hexo-bilibili-card
```

**引入代码**

```js
{% bilicard your_video_id %}
```

**效果与next主题兼容不太好，不推荐**

> 如深入理解计算机操作系统url：
>
>  https://www.bilibili.com/video/BV1ab411M7k8?from=search&seid=12268150136001117026
>
> seid号就是your_video_id

# 生成个人豆瓣数据

> 注意豆瓣插件只支持node的version为11.x.x
>
> 安装豆瓣后，hexo发布只能使用 `hexo deploy`，不再可以用hexo d 发布

**安装豆瓣插件**

```shell
npm install hexo-douban --save
```

**查看插件帮助文档**

```shell
hexo douban -h
```

**生成数据**

```js
hexo douban -b -m  # 生成书籍、电影数据
```

**配置**

```json
douban:
  user: mythsman
  builtin: false # 是否将生成页面的功能嵌入hexo s和hexo g中，默认是false,另一可选项为true(1.x.x版本新增配置项)
  book:
    title: 'This is my book title'
    quote: 'This is my book quote'
  movie:
    title: 'This is my movie title'
    quote: 'This is my movie quote'
  game:
    title: 'This is my game title'
    quote: 'This is my game quote'
  timeout: 10000 
```







