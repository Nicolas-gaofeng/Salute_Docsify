## 图片问题

`使用Github或者Git作为图床，配置PicGo+Typora`

> 图床就是存储图片的服务器，允许你把图片上传到服务器上，通过链接进行访问。目前很多图床都是免费的，但是大多数图床都有存储容量限制，有的还需要为此购买一个域名备案，使用起来很拘束。使用Github作为图床的优点是免费不限容量配置简单，不担心厂商跑路问题。
>

## Gitee

1. 注册gitee账号，新建仓库

![image-20210105000225757](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004135.png)

2. 创建完成后点击右上角头像->设置->私人令牌->生成新令牌。 

![image-20210105000533227](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004234.png)

3. 点击提交 这时候会让你输密码，输入即可，然后保存生成的令牌！

   `注意！！！`这个Token只会显示一次，自己先保存下来，或者等后面配置好PicGo后再关闭此网页

## Github

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

## PicGo

> PicGo是一个图床管理软件，配置后可以很方便的进行图片上传的操作，还有很多插件的支持，例如上传图片自动压缩、添加水印等… … 最重要的是可以与Typora进行交互，实现书写markdown中粘贴即上传的效果！

1. PicGo在Github的页面：https://github.com/Molunerfinn/PicGo

### github配置

1. 下载安装好后，打开软件，选择【图床设置】->【GitHub设置】，跳转到如下界面：

![image-20210104225856072](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004520.png)

**配置说明：**

​	【仓库名】-> 指定图片存储在哪个仓库：`你的用户名/仓库(图床)名`。

​	【设定分支名】 -> 指定一个分支：master

​	【Token】 -> 通信标识：`步骤3生成的Token`

​	【指定存储路径】 -> 在仓库下具体存储路径，会自动创建此文件夹：`路径/`

​	【自定义域名】 -> 它的作用是，在图片上传后，PicGo 会按照【自定义域名+储存路径+上传的图片名】的方式生成访问链接，并放到粘					贴板上，因为我们要使用 jsDelivr 加速访问，所以可以设置为:`https://cdn.jsdelivr.net/gh/用户名/图床仓库名`

2. 点击确定，保存设置。根据需求设为默认图床。

### Gitee配置

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

## 配置CDN：jsDelivr

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

## Typora配置

> 进行如下配置后，可以在编写markdown时直接粘贴图片，Typora会调用PicGo，实现图片上传。

1. 要求Typora的版本在0.9.84及以上，版本低于此的，【偏好设置】-【版本更新】
2. 打开PicGo 【设置】 -【设置Server】，进行如下配置(一般都为默认)

![image-20210104230409614](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004548.png)

3. 打开Typora，选择【偏好设置】 - 【图像】

4. 进行如下设置

![format](https://gitee.com/zgf1366/pic_store/raw/master/img/20210105004603.png)

5. 点击验证图片上传选项，观察success是否为true。成功之后打开GitHub图床仓库，就可以看到两个Typora的图标了~说明配置非常成功。

6. 现在在Typora中粘贴图片，会自动上传到Github图床，并且自动替换连接，非常省心省事~~~