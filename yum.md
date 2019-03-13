
# Yum（ Yellow dog Updater, Modified）

## yum check-update

列出所有可更新的软件清单命令

## yum update

更新所有软件命令

## yum install [package_name]

仅安装指定的软件命令

## yum update [package_name]

仅更新指定的软件命令

## yum list [status] | grep [package name]

列出所有可安裝的软件清单命令
[status]\
installed 今もう入っているパッケージ\
extras インストールディスクには含まれていないエキストラパッケージ\
core インストールディスクに含まれているパッケージで、現在はインストールされていないもの。\
updates 現在システムにインストールされているパッケージで、アップデータが必要なもの。

## yum info [package name]

パッケージ情報を取得

## yum makecache

パッケージ情報の更新

## yum remove [package_name]

删除软件包命令

## yum search [keyword]

查找软件包 命令

## yum provides [file name]

特定のファイルが提供されているパッケージ名を調べる

## yum deplist [package name]

パッケージの依存関係を調べる

## yum clean

yum のキャッシュは/var/cache/yum にある。\
清除缓存命令:
yum clean packages: 清除缓存目录下的软件包\
yum clean headers: 清除缓存目录下的 headers\
yum clean oldheaders: 清除缓存目录下旧的 headers\
yum clean, yum clean all (= yum clean packages; yum clean oldheaders) :清除缓存目录下的软件包及旧的headers