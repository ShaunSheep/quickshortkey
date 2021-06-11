# 遗留问题

- [ ] ~~如何添加评论？~~[Gitalk](https://github.com/gitalk/gitalk)he [Disqus](https://docsify.js.org/#/zh-cn/plugins?id=disqus)都是国外的，需翻墙不推荐
- [ ] 如何记录阅读量？
- [x] ~~如何插入表情？参考[typora-markdown#eomji写法](http://idolcoder.gitee.io/quickshortkey/#/typora?id=%e6%8f%92%e5%85%a5emoji)~~
- [ ] 还有哪些有趣的插件？
- [x] ~~自定义二级目录？~~[^3]
- [x] ~~(如何显示数学公式)(https://github.com/upupming/docsify-katex)~~

# 入门类

参考[^1]

## 全局安装

```shell
npm i docsify-cli -g
```

## 初始化子目录

```shell
docsify init ./docs
```

## 启动预览服务

```shell
docsify serve
## 指定端口号
docsify serve --port 4321
```

# 编辑类

## 强调内容

```markdown
!> 一段重要的内容，可以和其他 **Markdown** 语法混用。
```

效果如下

!> 一段重要的内容，可以和其他 **Markdown** 语法混用。

## 普通提示

```markdown
?> _TODO_ 完善示例
```

?> _TODO_ 完善示例

## 任务列表

```markdown
- [ ] foo
- bar
- [x] baz
- [] bam <~ not working
  - [ ] bim
  - [ ] lim
```

效果如下：

- [ ] foo
- bar
- [x] baz
- [] bam <~ not working
  - [ ] bim
  - [ ] lim

# 配置类

?>所有插件列表在[这里](https://docsify.js.org/#/awesome)。

## 配置评论

目前使用的是`gittalk`，共遇到俩问题



!>问题1： `$docsify` is not defined at gitalk.min.js:1

问题原因：docsify实际初始化顺序位于gittalk之后，gittalk引用了一个空的docsify对象

问题解决：移动gittalk脚本的引入位置，将其放在引入docsify脚本之后，并且初始化gittalk的顺序也放在docsify初始化之后。

!>问题2： gittalk Error: Bad credentials.

问题原因：当前页面未向github app授权

问题解决：

- 方法1：点击登录按钮，按提示给予github授权即可，如果还解决不了尝试方法2

- 方法2：

  - 从GitHub的 [Personal access token](https://github.com/settings/tokens) 页面，点击 [Generate new token](https://github.com/settings/tokens/new) 。

  - Select scopes：必选的选项为`repo`下的`repo:status`、`repo_deployment`和`public_repo`

  - 写到`gittalk`的`accessToken`初始化中,做法可以参考`gittalk`的`demo`的在线源码[^4]

    ```js
       var gitalk = new Gitalk({
            clientID: 'e46f6dec7c07145c652c',
            clientSecret: 'd1a0b627f9b76d21bd3080d1777d0aa0ad55dd83',
            accessToken: '6a2f4d91a1f188a2089e70c2a7b63628f3e9e664',
            repo: 'gitalk',
            owner: 'gitalk',
            admin: ['booxood', 'mamboer'],
            id: 'Demo',
            distractionFreeMode: true
          });
    ```

!>问题3：**Error: Not Found**

那一定是你信息没填对，`repo`那里，一定要填仓库名啊~

!>问题4：**Error: Validation Failed**

这里注意，docsify官网没有写出来，其实gitalk官网上提到

```objectivec
id: location.pathname,      // Ensure uniqueness and length less than 50
```

!>问题5：**未找到相关的issues进行评论**

这个问题不大，你点击下面，登入一下你的Guthub账户就好了

## 配置mermaid流程图

```js
// Import mermaid
 <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.css">
 <script src="//cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
// 注意脚本在初始化之前引入
var num = 0;
mermaid.initialize({ startOnLoad: false });

window.$docsify = {
  markdown: {
    renderer: {
      code: function(code, lang) {
        if (lang === "mermaid") {
          return (
            '<div class="mermaid">' + mermaid.render('mermaid-svg-' + num++, code) + "</div>"
          );
        }
        return this.origin.code.apply(this, arguments);
      }
    }
  }
}
```



## 配置黑夜模式

```shell
npm init
npm install docsify-darklight-theme 
```

该模式支持其他主题切换，切换的同时会丢掉黑夜白天切换功能

具体切换方式为：以下主题任选一种

```js
<!-- docsify-themeable styles-->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-simple.css" title="light">
    
<link rel="stylesheet alternative" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-simple-dark.css" title="dark">
```

### darklight模式下配置

```js
 window.$docsify = {

        darklightTheme: {
            siteFont : "PT Sans", #  Source Sans Pro| Helvetica
            defaultTheme : 'dark',
            codeFontFamily : 'Roboto Mono, Monaco, courier, monospace',
            bodyFontSize : '17px',
            dark: {
                accent: '#42b983',
                toogleBackground : '#ffffff',
                background: '#091a28',
                textColor: '#b4b4b4',
                codeTextColor : '#ffffff',
                codeBackgroudColor : '#0e2233',
                borderColor : '#0d2538',
                blockQuoteColour : '#858585',
                highlightColor : '#d22778',
                sidebarSublink : '#b4b4b4',
                codeTypeColor : '#ffffff',
                coverBackground : 'linear-gradient(to left bottom, hsl(118, 100%, 85%) 0%,hsl(181, 100%, 85%) 100%)',
                toogleImage : 'url(https://cdn.jsdelivr.net/npm/docsify-darklight-theme@latest/icons/sun.svg)'
            },
            light: {
                accent: '#42b983',
                toogleBackground : '#091a28',
                background: '#ffffff',
                textColor: '#34495e',
                codeTextColor : '#525252',
                codeBackgroudColor : '#f8f8f8',
                borderColor : 'rgba(0, 0, 0, 0.07)',
                blockQuoteColor : '#858585',
                highlightColor : '#d22778',
                sidebarSublink : '#b4b4b4',
                codeTypeColor : '#091a28',
                coverBackground : 'linear-gradient(to left bottom, hsl(118, 100%, 85%) 0%,hsl(181, 100%, 85%) 100%)',
                toogleImage : 'url(https://cdn.jsdelivr.net/npm/docsify-darklight-theme@latest/icons/moon.svg)'
            }
        }
    };
```



## 配置支持数学公式
[docsify-katex](https://github.com/upupming/docsify-katex)

```js
<!-- CDN files for docsify-katex -->
<script src="//cdn.jsdelivr.net/npm/docsify-katex@latest/dist/docsify-katex.js"></script>
<!-- or <script src="//cdn.jsdelivr.net/gh/upupming/docsify-katex@latest/dist/docsify-katex.js"></script> -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/katex@latest/dist/katex.min.css"/>
=======
## 配置代码高亮

?>docsify默认代码高亮支持如下语言：
- Markup - `markup`, `html`, `xml`, `svg`, `mathml`, `ssml`, `atom`, `rss`
- CSS - `css`
- C-like - `clike`
- JavaScript - `javascript`, `js`

​```js
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-php.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
```

可在[CDN](https://cdn.jsdelivr.net/npm/prismjs@1/components/)找到对应语法文件插入在脚本后面

如找到java\xml\shell\json：(用shell格式输出如下)

```shell
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-java.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-xml-doc.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-shell-session.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-json.min.js></script>

```

测试一段Java代码：

```xml
    private void bindAttrs(AttributeSet attrs) {
        TypedArray ta = null;
        try {
            ta = getContext().obtainStyledAttributes(attrs, R.styleable.NewCalendar);
            displayFormat = ta.getString(R.styleable.NewCalendar_dateFormat);
        } catch (Exception e) {
            Log.e("calendarview", e.toString());
        } finally {
            if (null != ta) {
                ta.recycle();
            }
            if (TextUtils.isEmpty(displayFormat)) {
                displayFormat = "MMM yyy";
            }
        }
    }
>>>>>>> 623bfd72e8a3cf5517db9b820b2b70258ef20718
```

## [docsify-tabs标签](https://jhildenbiddle.github.io/docsify-tabs/#/)

!>需翻墙，支持自定义CSS样式。

```markdown
<!-- tabs:start -->

#### ** Active State **

Hello!

#### ** Active State **

Bonjour!

#### ** Active State **

Ciao!

<!-- tabs:end -->
```

效果如下：

<!-- tabs:start -->

#### ** Active State**

Hello!

#### ** Java **

Bonjour!

#### ** Python **

Ciao!

<!-- tabs:end -->

## 我的配置文件

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-simple-dark.css">
...
<script>
	window.$docsify = {
      name: '快捷键-提升生产力', // 文档标题，显示在侧栏顶部。
      repo: 'https://github.com/ShaunSheep',
      loadNavbar: false,
	  search: 'auto', // 默认值
	  count:{
		countable:true,
		fontsize:'0.9em',
		color:'rgb(90,90,90)',
		language:'chinese'
	},
	  topMargin: 40, // 让你的内容页在滚动到指定的锚点时，距离页面顶部有一定空间。
      loadSidebar: true, // 加载自定义侧边栏
      maxLevel: 4, // 默认情况下会抓取文档中所有标题渲染成目录，可配置最大支持渲染的标题层级。
      subMaxLevel: 4, // 生成目录的最大层级
      mergeNavbar: true // 小屏设备下合并导航栏到侧边栏

    }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code"></script>
<script src="//unpkg.com/docsify-count/dist/countable.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```

# 参考

?><br>
[^1]: [docsify官方文档](https://docsify.js.org/#/)
<br>
[^2]: [docsify-tabs官方文档](https://jhildenbiddle.github.io/docsify-tabs/)
<br>
[^3]: [多页文档 (docsify.js.org)](https://docsify.js.org/#/zh-cn/more-pages)
<br>

[^4]:[Gitalk Demo | Aotu.io「凹凸实验室」](https://gitalk.github.io/)