# ubuatu-file-to-linspirer
专为领创管控的华为平板设计<br>
Windows直接网络共享会有"连接失败提示"<br>
本项目即为解决方法
====
一、原理
----
平板端:<br>
* 软件:利用华为自带文件管理中网络邻居<br>
* 网络邻居支持且仅支持SMB1.0协议<br>
* 所以，可供选择的方案较少<br>

电脑端:<br>
* Windows网络共享就是SMB协议，且平板可以搜到设备，但是会显示连接失败<br>
* 作为一种替代品，我选择用Linux虚拟机来网络共享<br>
* 教程里将会以Ubuntu为虚拟机系统为例<br>
* 通过命令行修改smb配置文件，添加账户<br>

二、虚拟机的安装
----
1.首先，要下载VMware虚拟机<br>
[点击下载VMware(571MB)](https://www.onlinedown.net/soft/2062.htm/)<br>
还需要一个Ubuntu的系统镜像文件<br>
[点击下载Ubuntu20.04.6(4.35GB)](http://mirrors.aliyun.com/ubuntu-releases/20.04/ubuntu-20.04.6-desktop-amd64.iso?spm=a2c6h.25603864.0.0.7f684509MplJ8J)<br>
2.VMware的激活自己搞，这里不再赘述<br>
3.选择新建虚拟机→镜像文件<br>
4.输入账号和密码，作为Ubuntu系统的登录账号和密码<br>
5.等待安装
6.在虚拟机设置中将网络连接方式修改为桥接模式<br>
一般默认是nat模式<br>
如果已经是桥接模式，则不需要修改<br>

三、samba的安装和配置
----
1.在命令行输入:(安装samba)
```
sudo apt-get install samba
```
2.选择一个文件夹，也可以将自己用户里的所有文件全部共享，这样更方便一些<br>
3.命令行切换到root用户:
```
sudo su
```
4.打开samba配置文件:
```
vi /etc/samba/smb.conf
```
5.接着就是最难操作的部分:<br>
用命令行vi文本编辑器修改配置文件<br>
前方高能!<br>
按键盘下键或用鼠标翻页，翻到最下方<br>
按 *i* 键进入插入模式<br>
然后输入:
```
[smbshare]
comment = myshare
path = /home/你的Ubuntu用户名
writable = yes
browsable = yes
```
其中，[]内的是显示名称<br>
comment是描述，可以随意写<br>
path下的路径一定要写对<br>
然后按 *enter* 键，输入 *:wq* 后按回车<br>
6.设置登录账户:
```
sudo smbpasswd -a 要设置的登录账户
```
然后按照提示输入登录用户名和密码<br>
7.输入以下命令重启smb服务:
```
sudo service smb restart
```
8.平板端检查是否能登录账户和访问文件
