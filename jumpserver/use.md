

###              jumpserver  使用 



#### 一  系统设置



邮件设置：点击页面上边的 "邮件设置" 按钮, 进入邮件设置页面，填写相关内容





![](images/系统邮件.png)







#### 二   资产管理



创建资产主机



![](images/资产.png)





#### 三  管理用户



*  管理用户是资产（被控服务器）上的root，或拥有 NOPASSWD: ALL sudo权限的用户， Jumpserver使用该     用户来推送系统用户、获取资产硬件信息 等。


创建管理用户



![](https://github.com/yunwei12345/smartgobook/raw/master/jumpserver/images/管理user.png)





   

*    系统用户"是 Jumpserver 跳转登录资产时使用的用户

  创建系统用户





![](images/系统user.png)









#### 四  权限管理



*  资产授权

把资产授权给用户后, 用户才能在 "我的资产" 里面看到资产, 配置正确后用户才能正常连接资产



创建授权规则



![](images/权管.png)





#### 五  连接远程资产主机（命令行)



```
ssh -p2222 smartgotest@192.168.150.48
```





 ![](images/connect.png)







#### 六    web 终端管理远程资产主机



*   Web 终端是资产使用界面, 管理员和用户都是从这里登录到资产上, 执行操作。点击资产名字连接资产, 点
  击"Server"下的"Disconnect"断开资产连接。




![](images/web.png)











