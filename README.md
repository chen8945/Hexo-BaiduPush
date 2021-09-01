# 自动提交网址给百度

## 前言

其实这个项目只是我自己发现了新大陆，然后自己搞了搞，本以为搞不出来，然而功夫不负有心人，我居然成功了。使用的语言是`django`这个🐂🖊哄哄的web框架。

如果图片不能查看的话，请移步到我的博客[https://www.antmoe.com/2020/01/31/zi-dong-ti-jiao-bai-du-lian-jie/](https://www.antmoe.com/2020/01/31/zi-dong-ti-jiao-bai-du-lian-jie/)或者查看项目中`文章图片`目录

## 使用

### 第一步 网址生成

首先你的hexo博客要装有`hexo-baidu-url-submit`这个[插件](https://github.com/huiwang/hexo-baidu-url-submit)。如果没有安装，请自行百度去安装这里不再过多赘述。并确保能够正常工作。确定你生成的目录public有一个叫`baidu_urls.txt`（如果你没有改名的话）。并且里边的内容是你的文章的地址。

![1.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg2qshqlgj20qs0jqace.jpg)

### 第二步 注册账号

这里我使用的是`LeanCloud`，虽然每天强制休息6小时，但足够了。除非你告诉我你想24小时都提交。官网地址[https://www.leancloud.cn/](https://www.leancloud.cn/)

如果你是第一次注册，那么你需要到设置里去完成实名认证，并且验证邮箱。假如这些你都完成了，那么我们进行第三步。

### 第三步 部署服务

1. 点击左上角的应用，然后点创建应用。

   ![2.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg0uur7k6j20s80a03yt.jpg)

2. 应用的名称可以随便写，我们就选择开发版，然后点击创建

   ![3.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg0vv07vmj20gn0c2aac.jpg)

3. 配置地址和环境变量（云引擎->设置）

   - 其中代码库的地址写`https://github.com/sviptzk/Hexo-BaiduPush.git`

   - 自定义环境变量

     - `BAIDU_URLS`

       这是你第一步生成的网址文件，将其部署成功后，将网址复制下来，例如`https://www.antmoe.com/baidu_urls.txt`

     - `STATIONMASTER`

       这是百度站长工具的提交地址。

       提交地址`https://ziyuan.baidu.com/linksubmit/index`

       ![5.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg19bewzwj210y0lzgn8.jpg)

     - `BEARPAW`

       这是熊掌号的提交地址，没有可以不写。乱写可能导致程序无法运行。

       获取地址`https://ziyuan.baidu.com/ydzq/includeweek?officeId=1635935633635770`

       这里建议使用周级，不建议天级，因为天级有每日次数限制，可以自行决定需要提交的网址。

       ![6.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1a8tjjgj20zh0iamz8.jpg)

   - 再点击申请Web主机域名。

     可以绑定自己的独立域名，也可以使用分发的。web页面主要是查看提交记录的。**这里强烈建议申请**

   

   ![7.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1d0lyw2j218x0ps40d.jpg)

   

4. 创建好了之后进入点击云引擎->部署->Git源码部署

   ![4.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg0xo9xfij214g0gn0to.jpg)

5. 填写好后，点击部署

   ![8.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1f82qgpj21g00k03zm.jpg)

6. 等待完成

   可以关闭这个窗口，然后到应用日志中查看进度。过程稍微有点慢，可以倒杯咖啡来喝了😄。

   ![9.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1l40h1uj20gc09wmx5.jpg)

   ![10.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1math61j213y0iumyy.jpg)

7. 部署完成

   可以看到最后输出的部署成功

   ![11.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1shvssnj21160nkwh5.jpg)

8. 项目部署完成后，可以通过申请的域名访问web地址。

   ![12.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1um4ed7j21130mt0v5.jpg)

   访问这个域名，可以看到登录界面。

   ![13.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg1vew3r8j212m0lzwye.jpg)

   其实这个页面我是在百度上找个，找回密码跟记住密码都没写，所以记住密码还是靠浏览器吧。找回密码就跟不存在了，直接修改数据库即可。

9. 添加账户

   进入`_User`表中，点击添加行，然后按要求填写即可

   ![14.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg2097klyj20jz0gbglv.jpg)

10. 登录后台

    可以用刚才添加的账号密码进行登录了。如果一切顺利的话，会看到这个界面

    ![15.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg21h81hbj20x9090weq.jpg)

    点击手动提交，就会进行一次手动将网址提交给百度。

    ![16.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg22nt1uwj20wu07qjro.jpg)

11. 设置定时任务

    ![17.png](https://tva1.sinaimg.cn/large/832afe33ly1gbg26b0jwfj212t0is0u2.jpg)

    时间采用的是cron表达式，不懂的童鞋请自行百度。

    创建完成后如果任务不是启用状态请点击启用。

## 开发

如果想二次开发~~不可能的，我自己都看不懂我写的代码~~，可以`clone`下代码进行二次开发。

说实话，代码是看着官方文档一点一点拼的，我自己都看不懂。期待有大佬能够二次开发，写一个更好的出来。

## 最后

**原创不易，转载请标明出处**，同时如果如果我的文章让你得到帮助，那么赞赏给作者一杯咖啡喝吧！

![Wechat](https://tva1.sinaimg.cn/large/832afe33ly1gbg2elhxyhj20v216mq5t.jpg)
![AliPay](https://tva1.sinaimg.cn/large/832afe33ly1gbg2elkxi6j20u01ao45r.jpg)

