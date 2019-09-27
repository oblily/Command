
# イメージ管理用(image)

## docker images

列出本地docker环境的所有image

## docker image pull XX

DockerイメージXXをDocker Hubから取得

## docker image ls

Dockerイメージの一覧を表示

## docker image inspect image-id

Dockerイメージの詳細を表示

## docker image tag

### docker image tag RepoXX goldkou/centos_hoge:1.0

Dockerイメージにタグ1.0をつけて別名保存

## docker image push

### docker image push goldkou/centos_hoge:1.0

Dockerイメージをレジストリ(デフォルトDocker Hub)へアップロード

## docker image rm

### docker image rm goldkou/centos_hoge:1.0

ローカルのDockerイメージの削除

## docker image save

### docker image save -o node.tar image-id

Dockerイメージをtarファイルに保存

## docker image load

### docker image load -i node.tar

saveで固めたtarからDockerイメージを作成

## docker image import

### docker image import tmp.tar

exportで固めたtarファイルからDockerイメージを作成

# コンテナ管理用(container)

## docker container ls -a

コンテナの一覧を表示

## docker container run image-name

Dockerイメージからコンテナを生成

## docker container stats container-id

stats：コンテナのリソース使用状況を表示,TOPの感じ

## docker container logs -t image-id

logs：コンテナ内の実行ログ確認

## docker container create image-repo

create：Dockerイメージからコンテナの生成

## docker container start container-id

start：コンテナの起動

## docker container stop container-id

stop：コンテナの停止

## docker container restart container-id

restart：コンテナの再起動

## docker container pause container-id

pause：コンテナの一時停止

## docker container unpause container-id

unpause：一時停止中コンテナの起動

## docker container rm container-id

rm：停止中コンテナの削除

## docker container attach container-id

attach：稼働中コンテナに接続 \
attachの場合はコンテナ内でシェルが動作していなければ接続することができない。\
Ctrl+C(あるいはexitコマンド)で抜けるとコンテナが停止してしまう(STATUSがExitedになる)ため、Exitedにしたくない場合は、Ctrl+Q+Pで抜ける。

## docker container exec -it container-id /bin/bash

exec：稼働中コンテナに接続 \
接続する際に稼働コンテナでPID=1のプロセスを実行するため、コンテナ内でシェルが動作している必要がない。\
Ctrl+C(あるいはexitコマンド)で抜けた後もSTATUSはUpのままで、接続時に起動したプロセスが停止するだけ。\
-itオプションはコンソール出力のお決まりのオプション。

## docker container top container-id

top：稼働中コンテナ内のプロセス一覧表示

## docker container port container-name

port：コンテナの公開ポート番号表示

## docker container rename old-container-name  new-container-name

rename：コンテナの名前変更

## docker container cp container-id:/etc/passwd /tmp

cp：コンテナとホストOS間でファイルとディレクトリのコピー

## docker container diff container-id

diff：Dockerイメージが生成されてからの変更情報を表示

## docker container commit container-id ubuntu_img

commit：変更があったコンテナからイメージを作成

## docker container export container-id > tmp.tar

export：コンテナをtarファイルに保存

# docker-compose

## docker-compose --version

版本确认

## docker-compose up

根据yml设定内容启动容器

## docker-compose stop

根据yml设定内容停止容器

## docker-compose down

根据yml设定内容停止并且销毁容器

# その他

## docker version

version：Dockerのバージョンを表示

## docker info

info：Dockerの実行環境情報を表示

## docker search

search：Docekrイメージの検索

## docker login

login：Docker Hubへログイン

## docker logout

logout：Docker Hubからログアウト

## docker ps -a

列出本地docker环境的所有容器

## docker run

使用image，启动容器

## docker stop

停止容器

## docker start

停止的容器再度启动

## docker pull dockername

默认从DockerHub中拉取image

## docker exec [option] container-name command

对指定的容器实行某种命令

## docker rm [option] container-name

容器的删除

## docker logs [option] container-name

容器执行log确认

## docker build [option] Dockerfile-path

image做成

## docker commit container-name container-image-name

container的现时点的状态保存到image

## docker push container-image-name[:tagname]

向仓库提交image


