# gitbook-template

借助模板仓库生成新的自定义 gitbook 仓库。现以新生成一个名为 gitbook-javascript-notes 仓库为例。

## Step1 初始化

- 克隆实例仓库到 gitbook-javascript-notes 文件夹

```shell
 git clone https://github.com/Jayee-Jiayi-Fu/gitbook-template.git gitbook-javascript-notes
```

- 删除模板历史记录

```shell
git cd gitbook-javascript-notes
rm -rf .git
```

## Step2 修改配置

- 在 GitHub 上新建一个远程仓库

- 修改配置文件
  修改 Travis CI 的 配置文件`.travis.yml`：
  recipients: 你的邮件地址
  REF: 你的 github 地址

根据个人喜好在 book.json 中修改 gitbook 的配置。

- 编辑你的 GitBook，关于 GitBook 的详细编辑教程请看[这里](https://chrisniael.gitbooks.io/gitbook-documentation/content/)

## Step3 远程提交

- 初始化本地仓库，并提交变更

```shell
git init
git add .
git commit -m "Initial commit"
```

- 添加远程分支到本地仓库，然后 push 到远程仓库：

```shell
git remote add origin https://github.com/Jayee-Jiayi-Fu/gitbook-javascript-notes.git
git push -u origin master
```

## Step4 配置 Travis CI

- 给项目开启 Travis CI 服务
  若尚未安装 Travis CI，点击[这里](https://github.com/marketplace/travis-ci)进行安装。你可以在第一次安装的时候跟随指引选择所需仓库。
  若已经安装 Travis CI，可以到账号 `Settings > Applications > Installed GitHub Apps` 下找到 Travis CI 的图标，点击 `Configure` 按钮，然后在 `Select repositories` 下拉栏目中选择所需仓库，点击 `Save` 按钮保存。

选择成功后，页面跳转到 Travis CI 的仓库管理页面，可以看到 Travis CI 当前正在管理的仓库：

![repositories in Travis CI](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/repositories-in-Travis.JPG)

点击 `setting` 按钮进入仓库管理页面。添加 `Environment Variables` 全局变量 `TOKEN`，value 值需要在 GitHub 账号 > Setting > Developer settings > Personal access tokens 下，点击 `Generate new token`，选择 `repo` 后生成。

![github token](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/github-token.JPG)

## Step5 启动持续集成

- 上图中点击 `trigger build` 按钮，或者在 master 分支上再次修改项目并 push 到远端，都可以触发 Travis CI 进行持续集成。

  ![触发构建按钮](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/trigger-build.JPG)

- 它会根据 master 分支上的变更重构建 gitbook，然后推送到远程仓库的 gh-pages 分支上。

  ![新分支 gh-pages](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/ghpages.JPG)

* Travis CI 的对应仓库中，会显示详细的集成进度和最后的集成结果，如下图所示：

  ![集成结果](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/joblog.JPG)

* 最后还要在项目 `Settings` 中配置 `GitHub Pages`

  ![配置GitHub Pages](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/github-pages.JPG)

## Step6 同步 GitBook

如果需要在[GitBook](https://app.gitbook.com/)页面中同步编辑，操作如下：

- 建议直接授权个人 GitHub 账号登录 GitBook。然后点击 `Create a new space` 按钮新建一个与仓库同名的 gitbook：

  ![gitbook](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/create-gitbook.JPG)

- 进入编辑页面后，打开 GitHub 关联按钮，然后选择对应仓库：

  ![gitbook-github](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/gitbook-github.JPG)

  ![link-github](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/link-github.JPG)

- 成功连接仓库后，就可以进行正常编辑。编辑完后，点击保存按钮，就可以看到当前的变更信息。再点击 merge 按钮，变更就会在合并后被 push 到远程仓库，然后触发 Travis CI 集成。

  ![gitbook-merge](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/gitbook-merge.JPG)

## Step7 最终结果

GitHub Pages 中给出了最终 gitbook 的访问地址：https://jayee-jiayi-fu.github.io/gitbook-javascript-notes

![gitbook](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/gitbook.JPG)

## 附录

- GitBook 常用命令

安装 GitBook

```shell
$ npm install gitbook-cli -g
```

根据 SUMMARY.md 的目录结构初始化各个章节文件：

```shell
$ gitbook init
```

运行服务，在编辑内容后实时预览：

```shell
$ gitbook serve
```

服务器启动后，浏览器打开 http://localhost:4000 查看，撰写完后可以生成静态网站用来发布：

```shell
$ gitbook build
```

- GitBook 常用插件

|                                         插件名                                         | 功能说明                                                         |
| :------------------------------------------------------------------------------------: | :--------------------------------------------------------------- |
|                                        -sharing                                        | 去除默认分享插件                                                 |
|                                      sharing-plus                                      | 分享当前页面，比默认的 sharing 插件多了一些分享方式              |
|                                        -search                                         | 去除默认搜索插件                                                 |
|                                       -highlight                                       | 去除默认的代码高亮插件，通常会使用 prism 来替换                  |
|                                     -font-settings                                     | 去除默认的字体、字号、颜色设置插件                               |
|                                      -livereload                                       | 去除默认 GitBook 实时重新加载插件                                |
|                                        splitter                                        | 在左侧目录和右侧内容之间添加一个可以拖拽的栏，用来调整两边的宽度 |
|                                  expandable-chapters                                   | 收起或展开章节目录中的父节点                                     |
|                                       search-pro                                       | 高级搜索                                                         |
|                                          code                                          | 代码添加行号和复制按钮                                           |
|                                   include-codeblock                                    | 通过引用文件插入代码                                             |
|                                    copy-code-button                                    | 代码复制按钮                                                     |
|                                          todo                                          | 待做项                                                           |
|                                      insert-logo                                       | 插入 logo                                                        |
|                                     advanced-emoji                                     | 支持 emoji 表情                                                  |
|                                       emphasize                                        | 为文字加上底色                                                   |
|                                         prism                                          | 基于 Prism 的代码高亮                                            |
|       [highlight-pro](https://github.com/tkggcelt/gitbook-plugin-highlight-pro)        | 代码高亮插件                                                     |
|                                          ace                                           | 插入代码高亮编辑器                                               |
|                                    flexible-alerts                                     | 警报                                                             |
|                                      change_girls                                      | 可自动切换的背景                                                 |
|                                        sectionx                                        | 用于将页面分成多个部分，并添加按钮以允许读者控制每个部分的可见性 |
|                                   auto-scroll-table                                    | 表格滚动条                                                       |
|                                         popup                                          | 单击图片，在新页面查看大图                                       |
|                                        lightbox                                        | 点击图片可显示，大小不变                                         |
|                                     image-captions                                     | 抓取内容中图片的 alt 或 title 属性，在图片下面显示标题           |
|                                      click-reveal                                      | 默认隐藏，点击可显示                                             |
|                                     custom-favicon                                     | 修改标题栏图标                                                   |
|                                       accordion                                        | 手风琴，外部显示模块标题和显示箭头，点击箭头可显示里面的内容     |
|                                      hide-element                                      | 可以隐藏不想看到的元素，比如导航栏中 Published by GitBook        |
|                                         github                                         | 在右上角显示 github 仓库的图标链                                 |
|                                     github-buttons                                     | 显示 github 仓库的 star 和 fork 按钮                             |
|                                        editlink                                        | 内容顶部显示编辑本页 链接接                                      |
|                                     pageview-count                                     | 阅读量计数                                                       |
|              [page-treeview](https://github.com/aleen42/gitbook-treeview)              | 生成页内目录                                                     |
|  [simple-page-toc](https://github.com/stuebersystems/gitbook-plugin-simple-page-toc)   | 生成本页目录                                                     |
|                           book-summary-scroll-position-saver                           | 自动保存左侧目录区域导航条的位置                                 |
|                                    page-toc-button                                     | 悬浮目录                                                         |
|                                    ancre-navigation                                    | 悬浮目录和回到顶部                                               |
| [anchor-navigation-ex](https://github.com/zq99299/gitbook-plugin-anchor-navigation-ex) | 锚点导航                                                         |
|                                        anchors                                         | 标题带有 github 样式的锚点                                       |
|                                   back-to-top-button                                   | 回到顶部                                                         |
|                                          atoc                                          | 插入 TOC 目录                                                    |
|                                    tbfed-pagefooter                                    | 自定义页脚，显示版权和最后修订时间                               |
|       [page-footer-ex](https://github.com/zq99299/gitbook-plugin-page-footer-ex)       | 自定义页脚，显示版权和最后修订时间,可选择支持 markdown           |
|                                     page-copyright                                     | 页面页脚版权（内容比 tbfed-copyright 更丰富）                    |
|                                           ad                                           | 在每个页面顶部和底部添加广告或任何自定义内容                     |
|                                         donate                                         | 打赏插件                                                         |
|                                         disqus                                         | 添加 disqus 评论插件                                             |
|                                        duoshuo                                         | 使用多说评论                                                     |
|                                         baidu                                          | 使用百度统计                                                     |
|                                           ga                                           | 添加 Google 统计代码                                             |
|                                         chart                                          | 使用 C3.js 图表                                                  |
|                                      styles-sass                                       | 使用 SASS 替换 CSS                                               |
|                                      styles-less                                       | 使用 LESS 替换 CSS                                               |
|                                        sitemap                                         | 生成站点地图                                                     |
|                                     latex-codecogs                                     | 使用数学方程式                                                   |
|                                        mermaid                                         | 使用流程图                                                       |
|                                          mcqx                                          | 使用选择题                                                       |
|                                          fbqx                                          | 使用填空题                                                       |
|                                        spoiler                                         | 隐藏答案，当鼠标划过时才显示                                     |
|                                        youtubex                                        | 插入 YouTube 视频                                                |
|                                        redirect                                        | 页面跳转                                                         |
|                                        jsfiddle                                        | 插入 JSFiddle 组件                                               |
|                                         jsbin                                          | 插入 JSBin 组件                                                  |
|           [theme-fexa](https://github.com/tonyyls/gitbook-plugin-theme-fexa)           | 主题插件                                                         |

在 book.json 文件的 plugins 和 pluginsConfig 字段添加插件及相关配置。添加完后进行安装：

```shell
# 安装插件
$ gitbook install
```
