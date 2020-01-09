#安装LNMP执行

    wget -c http://soft.vpser.net/lnmp/lnmp1.2-full.tar.gz && tar zxf lnmp1.2-     full.tar.gz && cd lnmp1.2-full && ./install.sh lnmp 
    如需要安装LNMPA或LAMP，将./install.sh 后面的参数替换为lnmpa或lamp即可。

    如下载速度慢请更换其他下载节点，详情请看下载页面。LNMP下载节点具体替换方法。

#按上述命令执行后，会出现如下提示：

   #需要设置MySQL的root密码（不输入直接回车将会设置为root）如果输入有错误需要删除  时，可以按住Ctrl再按Backspace键进行删除。输入后回车进入下一步，如下图所示：

#这里需要确认是否启用MySQL InnoDB，如果不确定是否启用可以输入 y ，输入 y 表示启用，输入 n 表示不启用。默认为y 启用，输入后回车进入下一步，选择MySQL版本：

#输入MySQL或MariaDB版本的序号，回车进入下一步，选择PHP版本：

#输入PHP版本的序号，回车进入下一步，选择是否安装内存优化：

#可以选择不安装、Jemalloc或TCmalloc，输入对应序号回车。

#如果是LNMPA或LAMP的话还需要设置管理员邮箱

#再选择Apache版本


     提示"Press any key to install...or Press Ctrl+c to cancel"后，按回车键确认开始安装。 
      LNMP脚本就会自动安装编译Nginx、MySQL、PHP、phpMyAdmin、Zend Optimizer这几个软件。

安装时间可能会几十分钟到几个小时不等，主要是机器的配置网速等原因会造成影响。

#安装完成
    如果显示Nginx: OK，MySQL: OK，PHP: OK

        并且Nginx、MySQL、PHP都是running，80和3306端口都存在，并Install lnmp V1.2   completed! enjoy it.的话，说明已经安装成功。
      接下来按添加虚拟主机教程，添加虚拟主机，通过sftp或ftp服务器上传网站，将域名解析到VPS或服务器的IP上，解析生效即可使用。

#安装失败

如果出现类似上图的提示，则表明安装失败，说明没有安装成功！！需要用winscp或其他类似工具，将/root目录下面的lnmp-install.log下载下来，到LNMP支持论坛发帖注明你的系统发行版名称及版本号、32位还是64位等信息，并将lnmp-install.log压缩以附件形式上传到论坛，我们会通过日志查找错误，并给予相应的解决方法。


      默认LNMP是不安装FTP服务器的，如需要FTP服务器：https://lnmp.org/faq/ftpserver.html

#添加、删除虚拟主机及伪静态管理
     http://lnmp.org/faq/lnmp-vhost-add-howto.html

#eAccelerator、xcache、memcached、imageMagick、ionCube、redis、opcache的安装
     http://lnmp.org/faq/addons.html

#LNMP相关软件目录及文件位置
     http://lnmp.org/faq/lnmp-software-list.html

#LNMP状态管理命令
     http://lnmp.org/faq/lnmp-status-manager.html

#关于linux 下网站文件夹存在user.ini 文件不能删除的问题

    LNMP 1.2及更高版本防跨目录功能使用.user.ini，该文件在网站根目录下，可以修改open_basedir的值来设置限制目录的访问。.user.ini文件无法直接修改，而且是隐藏文件可能在winscp下可能无法看到，建议使用vim编辑器或nano编辑器进行修改。
    如要修或删除需要先执行：chattr -i /网站目录/.user.ini
    修改完成后再执行：chattr +i /网站目录/.user.ini