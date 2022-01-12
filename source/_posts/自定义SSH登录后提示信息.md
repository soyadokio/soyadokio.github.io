---
title: 自定义SSH登录后提示信息
date: 2020-06-12 09:47:00
updated: 2020-06-12 09:47:00
toc: false
comments: true
categories:
  - Linux
tags:
  - 强迫症
description: VPS整的SSH登录后提示信息既帅气又实用
---

CentOS 平台上有个简单的小功能：MOTD（Message of the day），可时用户登录 SSH 时原样输出用户指定内容。
例如修改 `/etc/motd` 为：
```
欢迎回来~
```

则下次登录成功后会打印：
```
root@11.22.33.44's password:
Last login: Fri Jul 13 05:29:14 2018 from 111.175.59.239
欢迎回来~
[17:47:46 root@soyadokio ~]# 
```

说明：上面是原样输出，可如果需要动态内容，就需要用到自启动命令打印内容来模拟MOTD的效果。

操作：新建 `/etc/profile.d/motd.sh` ，内容为当前目录下 `motd.sh` 的内容，则可达成如下效果：
```
root@11.22.33.44's password:
Last login: Fri Jul 13 05:29:14 2018 from 111.175.59.239
111.175.59.239 -> Wuhan, Hubei, China
Hostname:   soyadokio.com (11.22.33.44)
Processes:  43
Uptime:     1 days, 16 hours, 59 minutes
CPU load:   0.05 0.02 0.00
Memo usage: 14.72% of 512.00MB
Users logged in: 1
[17:47:46 root@soyadokio ~]# 
```

注意：本脚本需 `jq` 支持，安装可执行以下命令：
``` bash
yum install -y jq
```

附上自己的 [motd.sh](motd.sh):
``` bash
#!/bin/bash
b=`tput bold`
n=`tput sgr0`
c=`tput setaf 2`
c2=`tput setaf 4`
lastip=`last | awk 'NR==1{print}' | sed "s/.*\s\(\([0-9]\{1,3\}\.\)\{3\}[0-9]\{1,3\}\)\s.*/\1/g"`
json=`timeout 1 curl -s http://ip-api.com/json/$lastip`
if [[ `echo $json | grep -P "^\{.*\}$"` ]]; then
    status=`echo $json | jq -r ".status"`
    if [ $status == "success" ]; then
        city=`echo $json | jq -r ".city"`
        regionName=`echo $json | jq -r ".regionName"`
        country=`echo $json | jq -r ".country"`
        geolocation=`echo -e "$city, $regionName, $country"`
        if [ $country == "China" ]; then
            echo -e "$lastip -> $geolocation"
        else
            echo -e "$lastip -> $c2$geolocation$n"
        fi
    fi
fi

if [[ `ifconfig | grep -P "inet addr:"` ]]; then # CentOS6/Debian
    ips=`ifconfig | awk '/inet addr/ {gsub("addr:", "", $2); print $2}'`
    for ip in $ips; do
        if [[ `echo $ip | grep -P "(\d{1,3}\.){3}\d{1,3}"` ]]; then
            if [[ `echo $ip | grep -P "^127.0.0.1$"` ]]; then
                :
            else
                echo -e "${b}${c}Hostname${n}:   `hostname` ($ip)"
                break
            fi

        else
            :
#            echo "Invalid IP format"
        fi
    done
elif [[ `ifconfig | grep -P "inet:"` ]]; then # CentOS7
#    echo "don't support CentOS 7"
    echo -e "${b}${c}Hostname${n}:   `hostname`"
else
#    echo "don't know type of ifconfig"
    echo -e "${b}${c}Hostname${n}:   `hostname`"
fi
echo -e "$b${c}Processes$n:  `cat /proc/loadavg | cut -d"/" -f2| cut -d" " -f1`"
upt=`uptime | awk -F'( |,|:)+' '{if ($7=="min") m=$6; else {if ($7~/^day/) {d=$6;h=$8;m=$9} else {h=$6;m=$7}}} {print d+0,"days,",h+0,"hours,",m+0,"minutes"}'`
echo -e "$b${c}Uptime$n:     $upt"
mf=`cat /proc/meminfo | grep MemFree | awk {'print int($2)'}` # memory free
mt=`cat /proc/meminfo | grep MemTotal | awk {'print int($2)'}` # memory total
mu=$[mt-mf] # memory used
musage=`awk 'BEGIN{printf "%.2f\n",('$mu'/'$mt'*100)}'` # memory usage
echo -e "$b${c}CPU load$n:   `cat /proc/loadavg | cut -d" " -f1-3`"
echo -e "$b${c}Memo usage$n: ${musage}% of `awk 'BEGIN{printf "%.2f\n",('$mt'/1024)}'`MB"
echo -e "$b${c}Users logged in$n: `w | tail -n +3 | wc -l`"
```