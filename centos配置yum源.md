## centos 配置yum源
### 本地源
+   挂载一个iso的镜像
+   然后进入/etc/yum.reps.d/目录下，创建一个以 .repo结尾的文件，内容如下
    ```
    [base]
    name=cdrom
    baseurl=file:///mnt
    enabled=1
    gpgcheck=0
    ```
+   ```
    yum clean all 清空本地的yum源缓存
    yum repolist  重新生成元数据
    ```
***
### 网络源
1.  网易
    ```
    cd  /etc/yum.repos.d/
    mv  *.repo  repo_backup/
    wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
    yum clean all   # 清空yum缓存
    yum repolist    # 查看yum源的列表并生成相应的元数据缓存到本地
    ```
2.  阿里云
    ```
    wget http://mirrors.aliyun.com/repo/Centos-7.repo   
    ```
3.  清华
    ```
    清华大学yum源配置方法：在/etc/yum.repos.d/目录下新建一个xxx.repo文件，粘贴以下内容即可
    [base]
    name=CentOS-$releasever - Base
    baseurl=http://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/os/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

    #released updates
    [updates]
    name=CentOS-$releasever - Updates
    baseurl=http://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/updates/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

    #additional packages that may be useful
    [extras]
    name=CentOS-$releasever - Extras
    baseurl=http://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/extras/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

    #additional packages that extend functionality of existing packages
    [centosplus]
    name=CentOS-$releasever - Plus
    baseurl=http://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/centosplus/$basearch/
    gpgcheck=1
    enabled=0
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
    ```