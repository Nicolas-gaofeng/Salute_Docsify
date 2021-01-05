<div align=center>

![docsify](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105160036.jpeg)

</div>

## 写在前面

- 关于封面

  我是中国人，当然要打出我们的大国宝啦。另外这是文明致敬docsify的一种方式，搭配程序员都爱的学习网站logo风格，别有一番滋味在心头~


![鲁迅](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105155946.jpeg)


- 本地编译：

  Markdown编辑器使用[Typora](https://typora.io/)（推荐）

  主题使用[Drake](https://theme.typora.io/theme/Drake/)

  

- 联系我：

  微信：

  intereting1366

  邮箱：

  gaofeng_zgf@163.com

  nicolasgaofeng@gmail.com

  

- 声明：

  这是一份自己学习docsify从入门到踩坑到跑路的记录。

  如果本仓库存在的内容对您和您的利益产生损害，请立即私信，我们将在最短时间内对其做出处理。

  

- 鸣谢：

  如果文中出现错误，请与我联系。向你敬礼！
  
  
  
- 官方网址：

  https://docsify.js.org/#/zh-cn/

## 一、安装

### 1.1 nodejs安装

参照地址：https://nicolas-gaofeng.github.io/Salute_Nodejs/

### 1.2 docsify安装

cmd打开命令行全局安装docsify，输入以下命令：

```undefined
npm i docsify-cli -g
```

安装成功后显示：

![img](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105164847.webp)

### 1.3 初始化项目

在文件夹地址框输入cmd打开命令行输入以下命令：

```kotlin
docsify init ./docs
```

![image-20210105165040807](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105165040.png)

初始化成功后，可以看到 `./docs` 目录下创建的几个文件

- index.html 入口文件
- README.md 会做为主页内容渲染
- .nojekyll 用于阻止 GitHub Pages 会忽略掉下划线开头的文件

直接编辑 docs/README.md 就能更新网站内容，当然也可以写多个页面。

![image-20210105165307401](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105165307.png)

### 1.4 本地预览网站

运行一个本地服务器，通过 docsify serve 可以方便的预览效果，而且提供 LiveReload 功能，可以实时的预览。默认通过 [http://localhost:3000](https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A3000)访问。

```undefined
docsify serve docs
```

![image-20210105165418610](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105165418.png)

## 二、配置

### 2.1 name

name：文档标题，会显示在侧边栏顶部。打开 index.html 文件，在 script 标签中对 `window.$docsify` 进行配置，如下所示：

```js
window.$docsify = {
        name: 'Salute_Docsify',
        repo: 'https://github.com/Nicolas-gaofeng/Salute_Docsify',
}
```

### 2.1 Github Corner

通过设置index.html中window.$docsify的 repo 参数配置仓库地址或者 username/repo 的字符串，会在页面右上角渲染一个 [GitHub Corner](https://links.jianshu.com/go?to=http%3A%2F%2Ftholman.com%2Fgithub-corners%2F) 挂件，点击即可跳转到Github中对应的项目地址。

```xml
<script>
    window.$docsify = {
      name: 'Salute_Docsify',
      repo: 'https://github.com/Nicolas-gaofeng/Salute_Docsify'
    }
</script>
```

![image-20210105165942759](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105165942.png)

### 2.2 封面

#### 2.2.1 封面渲染

通过设置 index.html 中 window.$docsify 的 `coverpage` 参数，即可开启渲染封面的功能。

```xml
<script>
    window.$docsify = {
      name: 'docsify',
      repo: 'https://github.com/Nicolas-gaofeng/Salute_Docsify',
      coverpage: true
    }
</script>
```

封面的生成同样是从 markdown 文件渲染来的。开启渲染封面功能后在文档根目录创建 `_coverpage.md` 文件，在文档中编写需要展示在封面的内容。

```markdown
<!-- _coverpage.md -->

![logo](_media/icon.svg)

# docsify <small>3.5</small>

> 一个神奇的文档网站生成器。

- 简单、轻便 (压缩后 ~21kB)
- 无需生成 html 文件
- 众多主题

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#docsify)
```

#### 2.2.2 自定义背景

目前的背景是随机生成的渐变色，我们自定义背景色或者背景图。在_coverpage.md文档末尾用添加图片的 Markdown 语法设置背景。

```markdown
<!-- _coverpage.md -->

# docsify <small>3.5</small>

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#quick-start)

<!-- 背景图片 -->

![](_media/bg.png)

<!-- 背景色 -->

![color](#f0f0f0)
```

#### 2.2.3 封面作为首页

通常封面和首页是同时出现的，当然你也是当封面独立出来通过设置[onlyCover 选项](https://docsify.js.org/#/zh-cn/configuration?id=onlycover)。

- 类型: `Boolean`

只在访问主页时加载封面。

```js
window.$docsify = {
  onlyCover: false,
};
```

#### 2.2.4 多个封面

如果你的文档网站是多语言的，或许你需要设置多个封面。

例如你的文档目录结构如下

```text
.
└── docs
    ├── README.md
    ├── guide.md
    ├── _coverpage.md
    └── zh-cn
        ├── README.md
        └── guide.md
        └── _coverpage.md
```

那么你可以这么配置

```js
window.$docsify = {
  coverpage: ['/', '/zh-cn/']
};
```

或者指定具体的文件名

```js
window.$docsify = {
  coverpage: {
    '/': 'cover.md',
    '/zh-cn/': 'cover.md'
  }
};
```

### 2.3 Loading提示

初始化时会显示 `Loading...` 内容，你可以自定义提示信息。

```html
  <!-- index.html -->

  <div id="app">加载中</div>
```

如果更改了 `el` 的配置，需要将该元素加上 `data-app` 属性。

```html
  <!-- index.html -->
  <div data-app id="main">加载中</div>

  <script>
    window.$docsify = {
      el: '#main'
    }
  </script>
```

对比 [el 设置](https://docsify.js.org/#/zh-cn/configuration?id=el)。

### 2.4 导航与侧边栏设置

#### 2.4.1 导航栏

简单导航栏:简单的导航栏可以在 `index.html` 文件中直接定义：

```html
<body>
  <nav>
    <a href="#/">LeetCode 题解</a>
    <a href="http://jalan.space" target="_blank">我的博客</a>
  </nav>
  <div id="app"></div>
</body>
```

复杂导航栏:复杂导航可以通过 Markdown 文件配置。

首先配置 `loadNavbar` 为 `true`：

```html
<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
<script src="//unpkg.com/docsify"></script>
```

在 `./docs` 下创建一个 `_navbar.md` 文件，在该文件中使用 Markdown 格式书写导航：

```text
* 导航1
    * [子导航](nav1/child/)
* [导航2](nav2/)
```

#### 2.4.2 侧边栏

默认情况下，侧边栏会根据当前文章的标题生成目录。但也可以通过 Markdown 文档生成。

首先配置 `loadSidebar` 选项为 `true`：

```html
<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//unpkg.com/docsify"></script>
```

然后在 `./docs` 下创建 `_sidebar.md` 文件：

```markdown
* [简介](/)
* 数据结构
  * [数组](data-structure/array/)
  * [字符串](data-structure/string/)
  * [链表](data-structure/linked_list/)
  * 树
    * [递归](data-structure/tree/recursion/)
    * [层次遍历（BFS）](data-structure/tree/bfs/)
    * [前中后序遍历（DFS）](data-structure/tree/dfs/)
    * [其他](data-structure/tree/other/)
```

### 2.5 主题

直接打开 index.html 修改替换 css 地址即可切换主题，官方目前提供五套主题可供选择，模仿 [Vue](https://links.jianshu.com/go?to=https%3A%2F%2Fvuejs.org) 和 [buble](https://links.jianshu.com/go?to=https%3A%2F%2Fbuble.surge.sh) 官网订制的主题样式。还有 [@liril-net](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fliril-net) 贡献的黑色风格的主题。

```html
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/vue.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/buble.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/dark.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/pure.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/dolphin.css">
```

其他主题docsify-themeable又提供了三种样式可供选择：

> docsify-themeable是一个用于docsify的，简单到令人愉悦的主题系统.

[Defaults](https://links.jianshu.com/go?to=https%3A%2F%2Fjhildenbiddle.github.io%2Fdocsify-themeable%2F%23%2Fthemes%3Fid%3Ddefaults)

```html
<!-- Theme: Defaults -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-defaults.css">
```

![img](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105170842.webp)

[Simple](https://links.jianshu.com/go?to=https%3A%2F%2Fjhildenbiddle.github.io%2Fdocsify-themeable%2F%23%2Fthemes%3Fid%3Dsimple)

```html
<!-- Theme: Defaults -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-defaults.css">
```

![img](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105170903.webp)

[Simple Dark](https://links.jianshu.com/go?to=https%3A%2F%2Fjhildenbiddle.github.io%2Fdocsify-themeable%2F%23%2Fthemes%3Fid%3Dsimple-dark)

```html
<!-- Theme: Simple Dark -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-simple-dark.css">
```

![img](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105170921.webp)

另外还有一种在网上看到的样式：

```xml
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify-themeable@0/dist/css/theme-simple.css">
```

### 2.6 多页面

目前我创建的文档是单页面的，上下滚动即可浏览全部内容。如果想创建多个页面，即点击左侧侧边栏导航跳转到不同url，就需要配置多级路由，这一功能在docsify中也很容易实现，我们需要在index.html文件中的`window.$docsify`中开启loadSidebar选项：

```xml
<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//unpkg.com/docsify"></script>
```

然后在根目录创建自己的_sidebar.md文件，配置我们需要显示的页面。详细操作步骤参考[官方多页文档教程](https://links.jianshu.com/go?to=https%3A%2F%2Fdocsify.js.org%2F%23%2Fzh-cn%2Fmore-pages)。

注：配置了`loadSidebar`后就不会生成默认的侧边栏了。

### 2.7 插件

官方还提供了非常多实用的插件，比如说全文搜索、解析emoji表情、一键复制代码等等，完整版请参考[官方插件列表](https://links.jianshu.com/go?to=https%3A%2F%2Fdocsify.js.org%2F%23%2Fzh-cn%2Fplugins)。

#### 2.7.1 搜索插件

全文搜索插件会根据当前页面上的超链接获取文档内容，在 localStorage 内建立文档索引。默认过期时间为一天，也可以指定需要缓存的文件列表或者过期时间。

打开 index.html 文件，添加全文搜索配置项，并引入 search.min.js，如下所示：

```js
<body>
  <script>
    window.$docsify = {
      search: {
        paths: 'auto',
        placeholder: '搜索',
        noData: '找不到结果',
        depth: 3,
      },
    }
  </script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
</body>
```

保存后，就可以在浏览器上查看到效果。

![image-20210105172849712](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105172849.png)

#### 2.7.2 图片缩放

在 index.html 文件中引入 zoom-image.min.js 即可，如下所示：

```js
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
```

保存后，就可以在浏览器上查看到效果，鼠标放到一张图片上时会出现缩小或者放大的图标，点击后就可以改变图片的形态。

#### 2.7.3 复制到剪贴板

在所有的代码块上添加一个简单的 Click to copy 按钮来允许用户从你的文档中轻易地复制代码。在 index.html 文件中引入 docsify-copy-code 即可，如下所示：

```js
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code"></script>
```

保存后，就可以在浏览器上查看到效果。

![image-20210105173159331](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105173159.png)

#### 2.7.4 代码高亮

docsify 内置的代码高亮工具是 [Prism](https://link.zhihu.com/?target=https%3A//github.com/PrismJS/prism)。Prism 默认支持的语言如下：

- Markup - `markup`, `html`, `xml`, `svg`, `mathml`, `ssml`, `atom`, `rss`
- CSS - `css`
- C-like - `clike`
- JavaScript - `javascript`, `js`

Java 需要在 index.html 文件中添加额外的语法文件，如下所示：

```js
<script src="https://cdn.jsdelivr.net/npm/prismjs@1.22.0/components/prism-java.min.js"></script>
```

注意这里引入的文件，如果你要高亮 Python 代码，那么就要引入：

```js
<script src="//unpkg.com/prismjs/components/prism-python.js"></script>
```

保存后，就可以在浏览器上查看到效果。

## 三、部署

### 3.1 Github Pages

和 GitBook 生成的文档一样，我们可以直接把文档网站部署到 GitHub Pages 或者 VPS 上。

GitHub Pages 支持从三个地方读取文件

- `docs/` 目录
- master 分支
- gh-pages 分支

我们推荐直接将文档放在 docs/ 目录下，找到仓库的Settings设置页面

![image-20210105171340658](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105171340.png)

开启 GitHub Pages 功能并选择 master branch /docs folder 选项。

![image-20210105171420883](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105171420.png)

发布成功后会显示网站地址，通过这个地址即可在线访问你编写的技术文档了。

## 四、图片问题

`使用Github或者Git作为图床，配置PicGo+Typora`

> 图床就是存储图片的服务器，允许你把图片上传到服务器上，通过链接进行访问。目前很多图床都是免费的，但是大多数图床都有存储容量限制，有的还需要为此购买一个域名备案，使用起来很拘束。使用Github作为图床的优点是免费不限容量配置简单，不担心厂商跑路问题。
>

### 4.1 Gitee

1. 注册gitee账号，新建仓库

![image-20210105000225757](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004135.png)

2. 创建完成后点击右上角头像->设置->私人令牌->生成新令牌。 

![image-20210105000533227](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004234.png)

3. 点击提交 这时候会让你输密码，输入即可，然后保存生成的令牌！

   `注意！！！`这个Token只会显示一次，自己先保存下来，或者等后面配置好PicGo后再关闭此网页

### 4.2 Github

1. 注册Github账号这个不用多说了

2. 新建仓库

在Github主页点击左上方的new按钮，准备新建仓库

输入仓库名、仓库描述、选择仓库为公开的、初始化README文件，点击【Create repository】按钮创建仓库

![7313](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004446.png)



3. 生成一个Token

Token是服务端生成的一串字符串，以作客户端进行请求的一个令牌，客户端只需带上这个Token前来请求数据即可，无需带上用户名和密码。

Token的目的是为了减轻服务器的压力，减少频繁的查询数据库，使服务器更加健壮。

在主页点击右上角的个人头像，依次选择【Settings】-【Developer settings】-【Personal access tokens】，跳转到这个界面

![image-20210104224443384](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004500.png)

4. 点击【Generate new token】，输入登录密码，填写好描述，勾选【repo】，然后点击【Generate token】(拉到最底部可以看到)，生成一个Token。

![image-20210104224619540](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004508.png)`注意！！！`这个Token只会显示一次，自己先保存下来，或者等后面配置好PicGo后再关闭此网页

### 4.3 PicGo

> PicGo是一个图床管理软件，配置后可以很方便的进行图片上传的操作，还有很多插件的支持，例如上传图片自动压缩、添加水印等… … 最重要的是可以与Typora进行交互，实现书写markdown中粘贴即上传的效果！

1. PicGo在Github的页面：https://github.com/Molunerfinn/PicGo

#### 4.3.1 github配置

1. 下载安装好后，打开软件，选择【图床设置】->【GitHub设置】，跳转到如下界面：

![image-20210104225856072](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004520.png)

**配置说明：**

​	【仓库名】-> 指定图片存储在哪个仓库：`你的用户名/仓库(图床)名`。

​	【设定分支名】 -> 指定一个分支：master

​	【Token】 -> 通信标识：`步骤3生成的Token`

​	【指定存储路径】 -> 在仓库下具体存储路径，会自动创建此文件夹：`路径/`

​	【自定义域名】 -> 它的作用是，在图片上传后，PicGo 会按照【自定义域名+储存路径+上传的图片名】的方式生成访问链接，并放到粘					贴板上，因为我们要使用 jsDelivr 加速访问，所以可以设置为:`https://cdn.jsdelivr.net/gh/用户名/图床仓库名`

2. 点击确定，保存设置。根据需求设为默认图床。

#### 4.3.2 Gitee配置

1. 打开我们下载好的PicGo，点击插件设置，安装Gitee图床插件gitee-uploader，然后重启一下软件，点击图床设置，找到Gitee的图床。

![image-20210105000800925](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004404.png)

2. 然后点击图床设置中的gitee

![image-20210105001253189](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004424.png)

**配置参数说明：**

- repo: Gitee用户名/仓库名；
- branch: 分支名：默认master即可
- token: `Gitee私人令牌`
- path: 用于仓库下存储的目录
- customPath和customUrl可以不用填

### 4.4 配置免费CDN：jsDelivr

> CDN：内容分发网络。配置使得网络传输的更快，更稳定。
>
> jsDelivr：是一个免费开源的 CDN 解决方案

1. 新建GitHub仓库，参考步骤2
2. 克隆项目到本地(需要安装git)
3. 在本地右键->【Git Bash Here】，执行`git clone [复制的地址]`
4. 随便选择一个文件放到本地git库中，右键->【Git Bash Here】执行以下命令(第一次使用git需要指定邮箱和用户名)

```
git status					//查看状态
git add [文件]				//添加文件到暂存区
git commit -m "第一次提交" 	//提交到仓库
git push					//推送至远程仓库
1234
```

5. 在github项目主页面，点击【Create a new release】

![image-20210104230157964](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004532.png)

6. 自定义版本号，点击【Publish release】按钮发布

![image-20210104230251407](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004539.png)

配置完成，使用方法：`https://cdn.jsdelivr.net/gh/用户名/仓库名@版本号/文件路径`

### 4.5 配置Typora

> 进行如下配置后，可以在编写markdown时直接粘贴图片，Typora会调用PicGo，实现图片上传。

1. 要求Typora的版本在0.9.84及以上，版本低于此的，【偏好设置】-【版本更新】
2. 打开PicGo 【设置】 -【设置Server】，进行如下配置(一般都为默认)

![image-20210104230409614](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004548.png)

3. 打开Typora，选择【偏好设置】 - 【图像】

4. 进行如下设置

![format](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004603.png)

5. 点击验证图片上传选项，观察success是否为true。成功之后打开GitHub图床仓库，就可以看到两个Typora的图标了~说明配置非常成功。

6. 现在在Typora中粘贴图片，会自动上传到Github图床，并且自动替换连接，非常省心省事~~~