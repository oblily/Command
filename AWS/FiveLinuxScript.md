
# 查看主机网卡流量

<#!/bin/bash

while : ; do

time='date +%m"-"%d" "%k":"%M'

day='date +%m"-"%d'

rx_before='ifconfig eth0|sed -n "8"p|awk '{print $2}'|cut -c7-'

tx_before='ifconfig eth0|sed -n "8"p|awk '{print $6}'|cut -c7-'

sleep 2

rx_after='ifconfig eth0|sed -n "8"p|awk '{print $2}'|cut -c7-'

tx_after='ifconfig eth0|sed -n "8"p|awk '{print $6}'|cut -c7-'

rx_result=$[(rx_after-rx_before)/256]

tx_result=$[(tx_after-tx_before)/256]

echo "$time Now_In_Speed: "$rx_result"kbps Now_OUt_Speed: "$tx_result"kbps"

sleep 2

done>

# 系统状况监控

<#!/bin/sh

IP=192.168.1.227

top -n 2| grep "Cpu" >>./temp/cpu.txt

free -m | grep "Mem" >> ./temp/mem.txt

df -k | grep "sda1" >> ./temp/drive_sda1.txt

//#df -k | grep sda2 >> ./temp/drive_sda2.txt

df -k | grep "/mnt/storage_0" >> ./temp/mnt_storage_0.txt

df -k | grep "/mnt/storage_pic" >> ./temp/mnt_storage_pic.txt

time=`date +%m"."%d" "%k":"%M`

connect=`netstat -na | grep "219.238.148.30:80" | wc -l`

echo "$time $connect" >> ./temp/connect_count.txt>

# 监控主机的磁盘空间,当使用空间超过90％就通过发mail来发警告

<#!/bin/bash

//#monitor available disk space

SPACE='df | sed -n '/ / $ / p' | gawk '{print $5}' | sed 's/%//'

if [ $SPACE -ge 90 ]

then

xxx@gmail.com

fi>

# 监控CPU和内存的使用情况

<#!/bin/bash

//#script to capture system statistics

OUTFILE=/home/xu/capstats.csv

DATE='date +%m/%d/%Y'

TIME='date +%k:%m:%s'

TIMEOUT='uptime'

VMOUT='vmstat 1 2'

USERS='echo $TIMEOUT | gawk '{print $4}' '

LOAD='echo $TIMEOUT | gawk '{print $9}' | sed "s/,//' '

FREE='echo $VMOUT | sed -n '/[0-9]/p' | sed -n '2p' | gawk '{print $4} ' '

IDLE='echo $VMOUT | sed -n '/[0-9]/p' | sed -n '2p' |gawk '{print $15}' '

echo "$DATE,$TIME,$USERS,$LOAD,$FREE,$IDLE" >> $OUTFILE>

# 全方位监控主机

<#!/bin/bash

DAT="`date +%Y%m%d`"

HOUR="`date +%H`"

DIR="/home/oslog/host_${DAT}/${HOUR}"

DELAY=60

COUNT=60

//# whether the responsible directory exist

if ! test -d ${DIR}

then

/bin/mkdir -p ${DIR}

fi

//# general check

export TERM=linux

/usr/bin/top -b -d ${DELAY} -n ${COUNT} > ${DIR}/top_${DAT}.log 2>&1 &

//# cpu check

/usr/bin/sar -u ${DELAY} ${COUNT} > ${DIR}/cpu_${DAT}.log 2>&1 &

//#/usr/bin/mpstat -P 0 ${DELAY} ${COUNT} > ${DIR}/cpu_0_${DAT}.log 2>&1 &

//#/usr/bin/mpstat -P 1 ${DELAY} ${COUNT} > ${DIR}/cpu_1_${DAT}.log 2>&1 &

//# memory check

/usr/bin/vmstat ${DELAY} ${COUNT} > ${DIR}/vmstat_${DAT}.log 2>&1 &

//# I/O check

/usr/bin/iostat ${DELAY} ${COUNT} > ${DIR}/iostat_${DAT}.log 2>&1 &

//# network check

/usr/bin/sar -n DEV ${DELAY} ${COUNT} > ${DIR}/net_${DAT}.log 2>&1 &

//#/usr/bin/sar -n EDEV ${DELAY} ${COUNT} > ${DIR}/net_edev_${DAT}.log 2>&1 &

放在crontab里每小时自动执行：

0 * * * * /home/check_xu.sh

这样便会在/home/oslog/host_yyyymmdd/hh目录下生成各小时cpu、内存、网络，IO的统计数据。

如果某个时间段产生问题了，就可以去看对应的日志信息，看看当时的主机性能如何。
