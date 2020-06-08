# Windows与Linux文件共享

# linux向windows共享文件

Samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Messages Block，信息服务块）是一种在局域网上共享文件和打印机的一种通信协议。


1. 安装samba：`sudo apt-get
install samba`

2. 创建samba共享账号和密码

      ` sudo smbpasswd -a linux_username`(注意 linux_username是你要共享文件的linux用户名)
      输入linux_username密码

3. 编辑samba配置文件

      ` sudo vim /etc/samba/smb.conf`
      在smb.conf文件添加如下文本

      ![](https://raw.githubusercontent.com/shiningpu/Picture-repository/master/Windows%E4%B8%8ELinux%E6%96%87%E4%BB%B6%E5%85%B1%E4%BA%AB1.png?token=AKRUBLKZKCJ56TPTRZIZDMC63H6JK)

      valid users 是新建的共享账户名，path输入自己的共享文件夹位置。[] 里面是自己的共享文件夹的名字。
      以上文本信息创建目录为/home/pi的共享文件夹pi，共享的linux用户名是pi。

4. 重启samba服务器

      `sudo service smbd restart`

5. 回到windows桌面，鼠标右键，新建快捷方式，文件位置为[\\IP_name\share_file]()，如下图所示。

  ![](F:\笔记\图库\Windows与Linux文件共享2.png)

6. 以上步骤完成后就可以在windows环境下对linux目录/home/pi文件夹中的文件进行操作。


# windows向linux共享文件

linux
使用mount 命令来挂载光盘镜像文件、移动硬盘、U盘以及Windows网络共享和UNIX
NFS网络共享等。cifs是Common Internet File System(通用网络文件系统)，mount.cifs用于挂载 CIFS 文件系统。

1.  进入windows系统，控制面板->网络和共享中心->更改高级共享设置->启用网络发现。

2.  鼠标右击要共享的文件夹，属性->共享，设置共享的属性。

3.  关闭windows防火墙

4.  进入linux
     `sudo apt-get install cifs-utils`
     `mkdir ~/Windows_Share`
     `sudo mount.cifs //NB-PUHUA/share /home/pi/Windows_Share –o
user=”puhua”`
     输入windows用户名puhua的密码
     命令中//NB-PUHUA/share是windows计算机名为NB-PUHUA的共享网络位置，共享文件夹是share,   /home/         pi/Windows_Share是挂载到linux系统里的挂载点，user=”puhua”表示共享文件夹的window用户名是                 puhua。

5.  df –h
查看挂载情况

参考：
[https://www.cnblogs.com/lyrichu/p/6867573.html](https://www.cnblogs.com/lyrichu/p/6867573.html)
[https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/)
