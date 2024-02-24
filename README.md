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

二、教程
----
首先，要下载VMware虚拟机<br>
还需要一个Ubuntu的系统镜像文件<br>
[点击下载Ubuntu20.04.6(4.35GB)](http://mirrors.aliyun.com/ubuntu-releases/20.04/ubuntu-20.04.6-desktop-amd64.iso?spm=a2c6h.25603864.0.0.7f684509MplJ8J)<br>
