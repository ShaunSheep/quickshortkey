# 快捷键Wiki

> 用快捷键提升生产力，让工具用的更顺手！

## 前言

如何做成一篇wiki？

早年写过一本Android的知识Wiki，挂在阿里云服务器上。当Markdown文章更新并提交到仓库的时候，直接被钩子触发，wiki服务自动部署，整个过程自动化执行下来倒也省事。

现在没服务器了，只能找些静态wiki实现方案比对选型：

| 名称                                                  | 演示                                                         | 优点                                                    | 缺点                             |
| ----------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------- | -------------------------------- |
| [MediaWiki](https://www.mediawiki.org/wiki/MediaWiki) | <img src="http://cdn.yangchaofan.cn/BlogGifRes/20210310/bNKkuK3kp9Hz.png"> | 主题简洁，开源免费                                      | 无法自定义                       |
| [DokuWiki](https://www.dokuwiki.org)                  | <img src="http://cdn.yangchaofan.cn/BlogGifRes/20210310/T71xC1AfJPJd.png"> | 模板插件多，可以自定义样式                              | 下载依赖文件较慢，频繁更新效率低 |
| [MinDoc](https://www.iminho.me)                       | <img src="http://cdn.yangchaofan.cn/BlogGifRes/20210310/Pv5OKvz02suH.png"> | 专业的文档管理系统，有开源版本                          | 付费才能解锁更多功能             |
| [docsify](https://docsify.js.org)                     | <img src="http://cdn.yangchaofan.cn/BlogGifRes/20210310/Ois6cWojts3n.png"> | 免费开源，主题5种可以diy                                | 单页面，不适合大型wiki系统       |
| [Wikitten](https://github.com/devaneando/Wikitten)    | <img src="http://cdn.yangchaofan.cn/BlogGifRes/20210310/rphqEdaiVkC0.png"> | 有hexo支持，也可以单独发布pages，树型文件夹访问较为传统 | 界面元素单一，无法自定义         |

最终选择了docsify，默认的vue主题很吸引人，界面年轻化且活泼，扩展功能相当简单，引入js，写一点config配置即可。

## 后记

做成这篇wiki主要参考了以下资料：

- [docsify官方文档](https://docsify.js.org/#/zh-cn/deploy)
- [docsify部署及配置 ](https://juemuren4449.com/archives/docsify-deploy-and-configuration)
- [有了docsify神器，从此爱上看文档](https://www.jianshu.com/p/4883e95aa903)