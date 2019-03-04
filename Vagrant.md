
# 仮想マシン

## vagrant version

バージョン確認 + 最新バージョンの表示 (vagrant -vはバージョン確認のみ)

## vagrant list-commands

vagrant コマンド

## vagrant global-status

全仮想マシンの一覧(名前、ステータス、パス)

--prune 全仮想マシンの一覧で削除済のものが出る場合

## vagrant up

仮想マシンの起動。vagrantfileのあるディレクトリ内で実行

## vagrant status

仮想マシンのステータスを表示

## vagrant ssh

仮想マシンにログイン

## vagrant ssh-config

sshログイン時の設定確認。IdentityFileは秘密鍵の場所

結果例

Host default \
  HostName 127.0.0.1 \
  User vagrant \
  Port 2222 \
  UserKnownHostsFile /dev/null \
  StrictHostKeyChecking no \
  PasswordAuthentication no \
  IdentityFile C:/Work/.vagrant/machines/ default/virtualbox/private_key \
  IdentitiesOnly yes \
  LogLevel FATAL

## vagrant halt

仮想マシンの終了(シャットダウン)

## vagrant suspend

仮想マシンの一時停止

## vagrant resume

仮想マシンの一時停止から復帰。

--provision オプションでプロビジョン実行

## vagrant reload

≒ halt ＆ up

--provision 設定ファイル(site.yml)を変更したらこのコマンドで反映

## vagrant destroy

仮想マシンの削除(boxは消えない)

## vagrant provision

仮想マシンは起動したままプロビジョニングのみ再度実行

# Box操作

## vagrant box list

boxの一覧を表示

## vagrant box add XX/XX

boxの追加。Vagrant Cloud、ローカルのbox、URLから取得から取得

## vagrant box update --box XX/XX

vagrant box updateでまとめて

## vagrant init BOX_NAME

初期化(Vagrantfileの作成)

## vagrant box remove XX/XX

boxの削除

--box-version 0.0.1 boxの削除(バージョン指定)

# スナップショット

## vagrant snapshot save <スナップショット名>

スナップショット作成

--provision 付けると強制的にプロビジョニング、 \
--no-provision 付けると強制的にプロビジョニングさせない

## vagrant snapshot restore <スナップショット名>

スナップショット復元。\
--[no-]provisionはsaveと同じ

## vagrant snapshot delete <スナップショット名>

スナップショットの削除

## vagrant snapshot list

名前付きスナップショットの一覧を表示

## vagrant snapshot push

使わない：スナップショット作成(名前は自動で付く)

## vagrant snapshot pop

使わない：スナップショット復元

# プラグイン

## vagrant plugin list

プラグイン一覧

## vagrant plugin expunge --reinstall

アンインストールして再インストール

## vagrant plugin install <プラグイン名1> <プラグイン名2>

インストール

## vagrant plugin uninstall <プラグイン名1> <プラグイン名2>

アンインストール

## vagrant plugin update [names...]

アップデート（名前省略で全てのプラグイン）

# Vagrant Cloud

## vaglant login

ログイン

## vagrant share

ローカル環境を公開。表示されるURLで外部からアクセス可能に。Ctrl + C で終了

## vagrant connect xxxxx

SSHなどでの接続も可能。セキュリティ的リスクあるが便利な場面も