
# which XX

查看 程序安装目录
例；which docker-compose

# echo $PATH

系统PATH确认

# export PATH=$PATH:/usr/local/XX

自分のパス追加

# sudo ln -s /usr/local/bin/XX /usr/bin/XX

シンボリックリンク追加
例；sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

# chmod +x XX

ファイルの実行権限追加
例：  chmod +x /usr/local/bin/docker-compose

# df / free

メモリ、ディスク使用率確認

# netstat -an | grep LISTEN

LISTENしているポート一覧取得.

# netstat -tan | grep ':8081' | awk '{print $6}' | sort | uniq -c

接続状態の確認と接続元IPのカウントをnetstatで行う。(8081ポート)

# netstat -tan | grep ':8081' | awk '{print $6}' │: 3100000 | sort | uniq -c

ポート8081の接続状態（接続数など） \
結果例： \
&nbsp;&nbsp;&nbsp;&nbsp;900 ESTABLISHED \
&nbsp;&nbsp;&nbsp;&nbsp;1 LISTEN \
&nbsp;&nbsp;&nbsp;&nbsp;1 TIME_WAIT

# vmstat 10 3

10秒ごとに３回でシステム情報を取得して表示する。

# systemctl status XX

プロセス運行情報 \
例：systemctl status redis

# tail -n 50 -f /var/log/nodejs/nodejs.log

ログの後ろから５０行取得

# service httpd status

サービスの起動確認
