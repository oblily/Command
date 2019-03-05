
# which redis-server

Confirm Redis server location.

# redis-server start

Run server.

# redis-cli shutdown

Server shutdown.

# netstat -tln | grep 63*

Check if Redis is on listen.

# systemctl status redis

Get server status.

# redis-cli

Access redis server.

# > select 0

0番目のDBにアクセス

# > keys *

登録されてるキーを表示 \
keys \*id* \
&nbsp;&nbsp;&nbsp;&nbsp;キー名にid を含むものを抽出

# > set XX AA

Register key.

# > get XX

値を取ってみる

# > del XX  

キーを消してみる

# > incr test_id

インクリメント

# > decrby test_id 4

4減らす

# > exists test_id

existsでtest_idの存在確認

# > exit

exist.
