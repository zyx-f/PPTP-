## 一、Windows 10客户端
#### 1.1 打开设置 > 网络和INTERNET > VPN > 添加VPN连接

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121095747705.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
#### 1.2 填写 VPN信息点击保存

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021012110043543.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121100549583.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
#### 1.3 右键单击VPN点击连接
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121100642177.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121100730465.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
## 二、Ubuntu / Linux客户端
#### 2.1 安装pptp客户端
```
sudo apt-get install pptp-linux
```
#### 2.2 初始化一个连接通道：mypptp
- mypptp本地通道名称
- `xxx.xxx.xxx.xxx`是pptp服务端的ip地址 根据实际情况填写
- 用户名和密码由服务端提供
```
sudo pptpsetup --create mypptp --server xxx.xxx.xxx.xxx --username 用户名 --password 密码 --encrypt --start
```
#### 2.3 指令执行成功输出示例
```
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2

CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
local  IP address 192.168.0.234
remote IP address 192.168.0.1
```
#### 2.4 查看连接是否成功
```
ip addr show
```
## 三、故障排查
#### 3.1 Windows 10 连接VPN后无法上外网
###### 3.1.1 打开控制面板 > 网络和Internet > 网络和共享中心 > 点击更改适配器设置
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121101221563.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)

###### 3.1.2 选择VPN > 右键 > 属性
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121101947696.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
###### 3.1.3 将“在远程网络上使用默认网关”取消掉，点击保存
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021012110213644.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121103329789.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
###### 3.1.4  在VPN设置界面断开连接后在重连就可以了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121103658207.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
#### 3.2 Windows 10 连接VPN后无法上外网，且点击属性无法开机
###### 3.2.1  找到rasphone.pbk文件用记事本打开，文件路径如下
- 在此之前一定要打开`显示隐藏文件`，不然会找不到。
- 路径中的Mr.zhang为自己电脑的用户名
-  `如果有多个VPN，用记事本打开每个VPN，查找VPN名字，确认`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121103958742.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
###### 3.2.2  查找`IpPrioritizeRemote`关键字，默认为1，改为0，保存即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121105207546.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbmd0aW5nMjA0MA==,size_16,color_FFFFFF,t_70)
#### 3.3 Ubuntu / Linux客户端无法ping通其它客户端
###### 3.3.1 添加路由
- `192.168.0.0/24`需要根据实际的`ppp0` ip来确定，如我现在ppp0的ip是192.168.0.234
```
route add -net 192.168.0.0/24  dev ppp0
```
###### 3.3.2 添加路由出现其它网络问题
- 删除路由
```
route del -net 192.168.0.0/24  dev ppp0
```
