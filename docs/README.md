## 一、Node.js

### 1. Node.js下载

官网下载地址：http://nodejs.cn/download/

根据自己需要下载对应的版本即可,我下载的是windows系统64位的版本。

![1.1.1](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003202.png)

### 2. Node.js安装

1.安装第一步直接点Next。

![1.2.1](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003221.png)

2.把选项打勾之后点击Next。

![1.2.2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003250.png)

3.设置安装路径，设置完成之后点击Next。

![1.2.3](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003259.png)

4.点击Next。

![1.2.4](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003306.png)

5.点击Install安装。

![1.2.5](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003315.png)

6.等待安装完成。

![1.2.6](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003321.png)

7.点击Finish完成安装。

![1.2.7](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003331.png)

3.查看node.js是否安装成功

npm 随安装程序自动安装，作用就是对 Node.js 依赖的包进行管理

windows下打开 cmd 输入以下命令行

```
node -v
npm -v
```

![1.3](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003348.png)

### 3.配置

4.1 配置全局目录

因为在执行例如npm install -g等命令全局安装的时候，默认会将模块安装在C:\Users\用户名\AppData\Roaming路径下的npm和npm_cache中，不方便管理且占用C盘空间，所以这里配置自定义的全局模块安装目录

在nodejs目录下，新建node_global、node_cache两个文件夹，然后运行以下2条命令：

```
npm config set prefix "D:\software\nodejs\node_global"
npm config set cache "D:\software\nodejs\node_cache"
```

注意！引号里的目录是你自己Node.js的安装地址

查看npm的本地仓库，输入命令

```
npm list -global
```

4.2 配置环境变量

在环境变量 -> 系统变量中新建一个变量名为 “NODE_PATH”， 值为“D:\Program Files\nodejs\node_modules”，如下图所示

![1.4.2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003527.png)

然后编辑用户变量里的Path，将相应npm的路径改为：D:\software\nodejs\node_global，如下：

![1.4.2.2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003535.png)



4.3 配置镜像站

输入命令

```
npm config set registry=http://registry.npm.taobao.org 
```

![1.4.3](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003551.png)

查看镜像站是否有用，看看能否获得vue的信息。如下图所示

```
npm info vue 
```

![1.4.3.2](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105003600.png)

配置完成。



## 二、图片问题

使用Github作为图床，配置PicGo+Typora

图床就是存储图片的服务器，允许你把图片上传到服务器上，通过链接进行访问。目前很多图床都是免费的，但是大多数图床都有存储容量限制，有的还需要为此购买一个域名备案，使用起来很拘束。使用Github作为图床的优点是免费不限容量配置简单，不担心厂商跑路问题。

1.注册git账号

![image-20210105000225757](C:\Users\zgf\AppData\Roaming\Typora\typora-user-images\image-20210105000225757.png)

创建完成后点击**右上角头像**->设置->私人令牌->生成新令牌。 

![image-20210105000533227](D:\我的坚果云\IT\8.图床\image-20210105000533227.png)

点击提交 这时候会让你输密码，输入即可

fc9e850b68052f5af560810eced38a3f

然后保存生成的令牌！！！一定要保存！！只会出现一次！！

然后我们打开我们下载好的PicGo
点击图床设置，没有看到Gitee的图床，这是因为我们还没有下载~
点击插件设置，安装Gitee图床插件**gitee-uploader**，然后重启一下软件，就可以看到了！

![image-20210105000800925](D:\我的坚果云\IT\8.图床\image-20210105000800925.png)

然后点击**图床设置**中的gitee

![image-20210105001253189](D:\我的坚果云\IT\8.图床\image-20210105001253189.png)

**配置参数说明：**

- repo: Gitee用户名/仓库名；
- branch: 分支名：默认master即可
- token: Gitee私人令牌
- path: 用于仓库下存储的目录
- customPath和customUrl可以不用填

1. 注册Github账号

- 这个不用多说了

2.新建仓库

1. 在Github主页点击左上方的new按钮，准备新建仓库
2. 输入仓库名、仓库描述、选择仓库为公开的、初始化README文件，点击【Create repository】按钮创建仓库

![image-20210104224236187](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\7313.png)



## 3.生成一个Token

Token是服务端生成的一串字符串，以作客户端进行请求的一个令牌，客户端只需带上这个Token前来请求数据即可，无需带上用户名和密码。

Token的目的是为了减轻服务器的压力，减少频繁的查询数据库，使服务器更加健壮。

在主页点击右上角的个人头像，依次选择【Settings】-【Developer settings】-【Personal access tokens】，跳转到这个界面

![image-20210104224443384](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\image-20210104224443384.png)

点击【Generate new token】，输入登录密码，填写好描述，勾选【repo】，然后点击【Generate token】(拉到最底部可以看到)，生成一个Token（很长很长~）。

![image-20210104224619540](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\image-20210104224619540.png)

1. 注意！！！这个Token只会显示一次，自己先保存下来，或者等后面配置好PicGo后再关闭此网页

77d62f4c9aaf7b844fc3a33cd1aa2a0ac5f539f6

## 4. 配置PicGo

> PicGo是一个图床管理软件，配置后可以很方便的进行图片上传的操作，还有很多插件的支持，例如上传图片自动压缩、添加水印等… … 最重要的是可以与Typora进行交互，实现书写markdown中粘贴即上传的效果！

1. PicGo在Github的页面：https://github.com/Molunerfinn/PicGo
2. 下载安装好后，打开软件，选择【图床设置】->【GitHub设置】，跳转到如下界面：

![image-20210104225856072](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\image-20210104225856072.png)

1. 配置说明

   1. 【仓库名】-> 指定图片存储在哪个仓库：`你的用户名/仓库(图床)名`。
   2. 【设定分支名】 -> 指定一个分支：master
   3. 【Token】 -> 通信标识：`步骤3生成的Token`
   4. 【指定存储路径】 -> 在仓库下具体存储路径，会自动创建此文件夹：`路径/`
   5. 【自定义域名】 -> 它的作用是，在图片上传后，PicGo 会按照【自定义域名+储存路径+上传的图片名】的方式生成访问链接，并放到粘贴板上，因为我们要使用 jsDelivr 加速访问，所以可以设置为:`https://cdn.jsdelivr.net/gh/用户名/图床仓库名`

2. 点击确定，保存设置。根据需求设为默认图床。

   ## 5.配置免费CDN：jsDelivr

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

   1. 在github项目主页面，点击【Create a new release】
   2. ![image-20210104230157964](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\image-20210104230157964.png)
   3. 自定义版本号，点击【Publish release】按钮发布

![image-20210104230251407](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\image-20210104230251407.png)

配置完成，使用方法：`https://cdn.jsdelivr.net/gh/用户名/仓库名@版本号/文件路径`



## 配置Typora

> 进行如下配置后，可以在编写markdown时直接粘贴图片，Typora会调用PicGo，实现图片上传。

1. 要求Typora的版本在0.9.84及以上，版本低于此的，【偏好设置】-【版本更新】
2. 打开PicGo 【设置】 -【设置Server】，进行如下配置(一般都为默认)
3. 

![image-20210104230409614](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\image-20210104230409614.png)

1. 打开Typora，选择【偏好设置】 - 【图像】

2. 进行如下设置

   ![img](D:\我的坚果云\IT\7.docsify\Salute_Docsify\image\format,png)

1. 点击验证图片上传选项，观察success是否为true。成功之后打开GitHub图床仓库，就可以看到两个Typora的图标了~说明配置非常成功。
2. 现在在Typora中粘贴图片，会自动上传到Github图床，并且自动替换连接，非常省心省事~~~



参考博客~[我的意大利炮呢](https://blog.csdn.net/qq_36376089)