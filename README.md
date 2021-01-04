

1.下载

官网下载地址：

http://nodejs.cn/download/

根据自己需要下载对应的版本,我下载的是windows系统64位的版本。

![image-20210104191950971](D:\我的坚果云\IT\7.docsify\1.1.1.png)

2. node.js安装

1.安装第一步直接点Next。

![image-20210104192102227](D:\我的坚果云\IT\7.docsify\1.2.1.png)

2.把选项打勾之后点击Next。

![image-20210104192138922](D:\我的坚果云\IT\7.docsify\1.2.2.png)

3.设置安装路径，设置完成之后点击Next。

![image-20210104192440462](D:\我的坚果云\IT\7.docsify\1.2.3.png)

4.点击Next。

![image-20210104192509037](D:\我的坚果云\IT\7.docsify\1.2.4.png)

5.点击Install安装。

![image-20210104192537418](D:\我的坚果云\IT\7.docsify\1.2.5.png)

6.等待安装完成。

![image-20210104192557243](D:\我的坚果云\IT\7.docsify\1.2.6.png)

7.点击Finish完成安装。

![image-20210104192632266](D:\我的坚果云\IT\7.docsify\1.2.7.png)

3.查看node.js是否安装成功

npm随安装程序自动安装，作用就是对Node.js依赖的包进行管理

打开cmd输入以下命令行

```
node -v
npm -v
```

![image-20210104193118926](D:\我的坚果云\IT\7.docsify\1.3.png)

4.配置

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

![image-20210104194232070](D:\我的坚果云\IT\7.docsify\1.4.2.png)

然后编辑用户变量里的Path，将相应npm的路径改为：D:\software\nodejs\node_global，如下：

![image-20210104194412170](D:\我的坚果云\IT\7.docsify\1.4.2.2.png)



4.3 配置镜像站

输入命令

```
npm config set registry=http://registry.npm.taobao.org 
```

![image-20210104194036603](D:\我的坚果云\IT\7.docsify\1.4.3.png)

查看镜像站是否有用，看看能否获得vue的信息。如下图所示

```
npm info vue 
```

![image-20210104194702169](D:\我的坚果云\IT\7.docsify\1.4.3.2.png)

配置完成。