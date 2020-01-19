> 参考链接:
- [超详细Hexo+Github博客搭建小白教程](https://godweiyang.com/2018/04/13/hexo-blog/#toc-heading-8)
- [使用hexo，如果换了电脑怎么更新博客？](https://www.zhihu.com/question/21193762/answer/79109280)

## 安装 Node.js
在 [Node.js 官网](https://nodejs.org/en/download/) 下载安装包，并安装。在命令提示符中使用以下命令查看版本号。
```bash
node -v
npm -v
```

## 安装并初始化 Hexo
依照以下流程完成 Hexo 的安装以及初始化。
- 在 Github 中创建名为 `<your username>.github.io` 的仓库。
- 创建一个名为 `hexo` 的分支，并把它设为默认分支，用于存放网站的模板文件。
- 将该仓库拷贝到本地文件夹。
```bash
git clone <your repo>
```
- 在本地仓库文件夹处右键进入该文件夹位置的 `Git Bash` ，依次执行以下命令。  
```bash
npm install hexo
hexo init
npm install
npm install hexo-deployer-git --save
```
这里由于命令 `hexo init` 命令只能在空文件夹中执行，因此直接在本地仓库文件夹执行会报错，有如下两种方法解决。
  - 新建一个文件夹，在该文件夹中执行 `hexo init` 命令，再将里面的文件拷贝到本地仓库文件夹。
  - 在本地仓库文件夹执行 `hexo init <folder name>` 命令，该命令会创建一个文件夹。
- 修改文件 `_config.yml` 中的参数。
```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
    type: git
    repo: <your repo URL>
    branch: master
```
- 向 Github 提交模板文件的改动，上一步改动的 `branch` 参数将自动把 Hexo 创建的静态文件提交到 `master` 分支。
```bash
git add .
git commit -m "..."
git push origin hexo
```
到这一步为止网站的模板文件操作已经结束了，可以使用以下命令检查生成的网页。
```bash
hexo g -d
hexo s
```
如果顺利，第一条命令将会生成静态文件并将网页推送到 GitHub 服务器，并且可以在 `https://<your username>.github.io/` 访问到。第二条命令会在本地生成网页预览，可以在 `local host:4000` 访问到。

## 修改主题
除了 Hexo 的初始默认主题，也可以使用其他主题。可以在 Github 搜索关键字 `hexo theme` 查看。  
- 将新主题克隆到 `themes` 文件夹。
```bash
hexo clean
git clone <theme repo> themes/<theme name>
```
- 按照主题的操作说明修改相关的参数。
- 推送主题的更新并在本地预览。
```bash
git add .
git commit -m "..."
git push origin hexo
hexo g -d
hexo s
```

## 更新文章
- 在本地仓库文件夹处右键进入该文件夹位置的 `Git Bash` ，执行以下命令。该命令会在路径 `/source/_posts` 下生成一个 `<article title>.md` 空文件。
```bash
hexo new post "<article title>"
```
- 使用以下命令推送网页以及在本地预览网页。
```bash
hexo g -d
hexo s
```

## 在新电脑中部署相关文件
如果文件丢失或者希望在一台新设备上更新文章，则按以下流程部署。
- 将网站的项目仓库拷贝到本地文件夹。
```bash
git clone <your repo>
```
- 在本地仓库文件夹处右键进入该文件夹位置的 `Git Bash` ，依次执行以下命令。  
```bash
npm install
```

## 常用命令
- Hexo
```bash
hexo init  # 初始化
hexo new post "<article title>"  # 新建文章
hexo g  # 生成静态文件
hexo d  # 部署网页到服务器
hexo s  # 生成本地网页预览
hexo clean  # 清楚缓存，更换主题时用
```
