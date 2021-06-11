# Android Studio

主要参考了[官方文档](https://developer.android.google.cn/studio/intro/keyboard-shortcuts?hl=zh-cn)，积累一些自己常用的快捷键。

# 运行

| 键名                   | 用途         |
| ---------------------- | ------------ |
| 编译                   | Ctrl+F9      |
| 编译并运行             | Shift+F10    |
| 应用代码更改           | Ctrl+Alt+F10 |
| 应用更改并重启Activity | Ctrl+F10     |

# 调试

| 键名                              | 用途          |
| --------------------------------- | ------------- |
| 调试                              | Shfit+F9      |
| 单步执行                          | F8            |
| 单步进入                          | F7            |
| 单步退出                          | Shift+F8      |
| 运行到光标位置                    | Alt+F9        |
| 评估表达式                        | Alt+F8        |
| 运行程序                          | F9            |
| 切换断点                          | Ctrl+F8       |
| <font color="red">查看断点</font> | Ctrl+Shift+F8 |



# 设计

| 键名              | 用途                                      |
| ----------------- | ----------------------------------------- |
| B                 | 在设计图和蓝图模式切换                    |
| O                 | 在竖屏和横屏模式切换                      |
| D                 | 切换设备                                  |
| R                 | 强制刷新                                  |
| E                 | <font color="red">切换渲染错误面板</font> |
| Ctrl+B            | 转到XML                                   |
| Ctrl+Shift+方向键 | 切换设计图、蓝图、XML                     |

# 重构

| 键名     | 用途         |
| -------- | ------------ |
| F5       | 复制当前内容 |
| F6       | 移动当前内容 |
| Shift+F6 | 重命名       |



# 文件

## 查看类

| 键名                            | 用途                                 |
| ------------------------------- | ------------------------------------ |
| ctrl+shift+N                    | 全局查找文件                         |
| Ctrl+Shift+A                    | 查找操作，操作是至如换行，插入，删除 |
| F4                              | 跳转到源代码                         |
| Ctrl+Enter                      | 跳转到源代码                         |
| Ctrl+E                          | 查看最近打开的文件弹出菜单           |
| Ctrl+Shift+E                    | 查看最近编辑的文件及源码位置弹出菜单 |
| Ctrl+Shift+BackSpace            | 转到上一个编辑位置                   |
| Ctrl+F4                         | 关闭活动标签页                       |
| Shift+Esc                       | 隐藏上一个活动工具窗口               |
| <font color="red">Ctrl+G</font> | 跳转到指定行                         |
| Ctrl+H                          | 打开类层次结构                       |
| Ctrl+Shift+H                    | 打开方法层次结构                     |
| Ctrl+Alt+H                      | 打开调用层次结构                     |

## 创建类

| 键名       | 用途             |
| ---------- | ---------------- |
| Alt+Insert | 快速创建模板文件 |



# 代码

## 查看类

| 键名             | 用途                       |
| ---------------- | -------------------------- |
| ctrl+F           | 当前页查找变量             |
| ctrl+shift+F     | 全局查找变量               |
| ctrl+shift+N     | 全局查找文件               |
| 双击shift        | 搜索全部内容               |
| Ctrl+Shift+“+/-” | 收起或展开该位置代码库     |
| Ctrl+Q           | 快速查看文档               |
| Ctrl+P           | 展示指定方法的参数         |
| Ctrl+B           | 转到调用者的实现位置       |
| Ctrl+Shift+[     | 从当前位置到代码块起始位置 |
| Ctrl+Shift+]     | 到结束位置                 |
| Ctrl+Backspace   | 从当前位置删除到开头位置   |
| F2               | 下一个突出的错误           |



## 编辑类

| 键名            | 用途         |
| --------------- | ------------ |
| ctrl+r          | 替换变量名   |
| Ctrl+Y          | 快速删除行   |
| Ctrl+D          | 快速复制行   |
| Ctrl+space      | 代码补全     |
| Ctrl+Shift+spae | 智能代码补全 |
| Ctrl+Alt+O      | 优化导包     |
| Alt+Enter       | 快速修复代码 |
| Ctrl+Alt+L      | 格式化代码   |
| Ctrl+Alt+I      | 自动缩进     |



## 创建类

| 键名          | 用途                                 |      |
| ------------- | ------------------------------------ | ---- |
| Ctrl + Alt +F | 将局部变量转为全局变量               |      |
| Alt+Insert    | 快速生成模板代码（getter、setter、） |      |
| Ctrl+I        | 实现方法                             |      |
| Ctrl+Alt+T    | 快速生成控制语句                     |      |



# 配置

## 配置文件模板

File->Setting->Editor->Live Templates->click "+" add a group ->click "+" add a template

->Abbreviation is shortkey to fast generate a piece  of code

->Edit variables is set value for `$value$`

# 插件

| 名称 | 用途 | 用法 |
| ---- | ---- | ---- |
|      |      |      |



# 异常问题

## AndroidStudio无法打开

**问题根源：**其实是某些插件不支持高版本,然后就启动不起来了,说实话直接启动不起来显得一点也不人性化

**解决方法：**C:\Users\{user}\AppData\Roaming\Google\AndroidStudio4.1\plugins 备份后全部粉碎删除，如果无法删除，请重启电脑后尝试删除

