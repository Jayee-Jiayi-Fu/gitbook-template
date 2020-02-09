# gitbook-template

借助模板仓库生成新的自定义 gitbook 仓库。现以新生成一个名为 gitbook-javascript-notes 仓库为例：

## Step1:

- 克隆实例仓库到 gitbook-javascript-notes 文件夹

```shell
 git clone https://github.com/Jayee-Jiayi-Fu/gitbook-template.git gitbook-javascript-notes
```

- 删除模板历史记录

```shell
git cd gitbook-javascript-notes
rm -rf .git
```

## Step2:

- 在 GitHub 上新建一个远程仓库

- 修改配置文件
  修改 Travis CI 的 配置文件`.travis.yml`：
  recipients: 你的邮件地址
  REF: 你的 github 地址

根据个人喜好在 book.json 中修改 gitbook 的配置。

- 编辑你的 GitBook，关于 GitBook 的详细编辑教程请看[这里](https://chrisniael.gitbooks.io/gitbook-documentation/content/)

## Step3：

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

## Step4:

- 给项目开启 Travis CI 服务
  若尚未安装 Travis CI，点击[这里](https://github.com/marketplace/travis-ci)进行安装。你可以在第一次安装的时候跟随指引选择所需仓库。
  若已经安装 Travis CI，可以到账号 `Settings > Applications > Installed GitHub Apps` 下找到 Travis CI 的图标，点击 `Configure` 按钮，然后在 `Select repositories` 下拉栏目中选择所需仓库，点击 `Save` 按钮保存。

选择成功后，页面跳转到 Travis CI 的仓库管理页面，可以看到 Travis CI 当前正在管理的仓库：

![repositories in Travis CI](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/repositories-in-Travis.JPG)

点击 `setting` 按钮进入仓库管理页面。添加 `Environment Variables` 全局变量 `TOKEN`，value 值需要在 GitHub 账号 > Setting > Developer settings > Personal access tokens 下，点击 `Generate new token`，选择 `repo` 后生成。

![github token](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/github-token.JPG)

## Step5:

- 上图中点击 `trigger build` 按钮，或者在 master 分支上再次修改项目并 push 到远端，都可以触发 Travis CI 进行持续集成。

  ![触发构建按钮](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/trigger-build.JPG)

- 它会根据 master 分支上的变更重构建 gitbook，然后推送到远程仓库的 gh-pages 分支上。

  ![新分支 gh-pages](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/gh-pages.JPG)

* Travis CI 的对应仓库中，会显示详细的集成进度和最后的集成结果，如下图所示：

  ![集成结果](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/joblog.JPG)

* 最后还要在项目 `Settings` 中配置 `GitHub Pages`

  ![配置GitHub Pages](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/github-pages.JPG)

## Step6:

如果需要在[GitBook](https://app.gitbook.com/)页面中同步编辑，操作如下：

- 建议直接授权个人 GitHub 账号登录 GitBook。然后点击 `Create a new space` 按钮新建一个与仓库同名的 gitbook：

  ![gitbook](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/create-gitbook.JPG)

- 进入编辑页面后，打开 GitHub 关联按钮，然后选择对应仓库：

  ![gitbook-github](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/gitbook-github.JPG)

  ![link-github](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/link-github.JPG)

- 成功连接仓库后，就可以进行正常编辑。编辑完后，点击保存按钮，就可以看到当前的变更信息。再点击 merge 按钮，变更就会在合并后被 push 到远程仓库，然后触发 Travis CI 集成。

  ![gitbook-merge](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/gitbook-merge.JPG)

## Step7:

GitHub Pages 中给出了最终 gitbook 的访问地址：https://jayee-jiayi-fu.github.io/gitbook-javascript-notes

![gitbook](http://q5frcy1n7.bkt.clouddn.com/images/gitbook/gitbook-template/gitbook.JPG)
