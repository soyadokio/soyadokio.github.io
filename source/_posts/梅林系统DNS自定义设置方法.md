# 梅林系统DNS自定义设置方法

## 用途

举个例子，我家有多台网络设备：

* 192.168.0.1 光猫

* 192.168.1.1 路由器

* 192.168.1.2 家庭服务器

* 192.168.1.3 影音库

这样每次访问都输入IP就有些麻烦，于是就自己解析几个域名方便点，比如将域名`lyq.com`解析为`192.168.1.1`，这样下次再访问路由器时就不需要输入`192.168.1.1`，直接输入域名`lyq.com`就可以了。

## 步骤

1. 使用浏览器访问路由器管理界面并登录

1. 系统管理 - 系统设置 - `Enable JFFS custom scripts and configs` 设置为`是`；`Enable SSH` 设置为`LAN only`，并点击页面下方应用本页面设置按钮

1. AiProtection智能网络卫士 - DNS Filtering - `Enable DNS-based Filtering` 设置为`OFF`，并点击页面下方应用本页面设置按钮

1. 内部网络（LAN） - DHCP服务器 - `DNS Server 1` 设置为**本路由器的IP**，`DNS Server 2` 留空即可，`Forward local domain queries to upstream DNS` 设置为`否`，并点击页面下方应用本页面设置按钮

1. 使用putty等工具登录SSH，用户名密码与登录路由器Web页面相同

    ```shell
    ssh admin@192.168.1.1
    ```

1. 创建自定义DNS配置文件

    ```shell
    vi /jffs/configs/dnsmasq.d/dnsmasq.conf
    ```

1. 添加需要的解析内容，规则如下：

    * 单域名对应单IP时：

        ```text
        address=/gm.home/192.168.0.1
        address=/lyq.home/192.168.1.1
        address=/fwq.home/192.168.1.2
        address=/yyk.home/192.168.1.3
        ```

    * 多域名对应单IP时：

        ```text
        address=/gm.home/guangmao.home/192.168.0.1
        address=/lyq.home/luyouqi.home/192.168.1.1
        address=/fwq.home/fuwuqi.home/192.168.1.2
        address=/yyk.home/yingyinku.home/192.168.1.3
        ```

1. 执行重启DNS服务命令后立即生效

    ```shell
    service restart_dnsmasq
    ```
