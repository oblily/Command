
# tmuxコマンド

## % tmux ls : セッション一覧を確認

## % tmux a : 最後に使用したセッションにアタッチ

## % tmux a -t "セッション名" : 指定したセッションにアタッチ

## % tmux kill-session -t "セッション名" : セッション終了

## tmux list-session

## tmux list-window

# bind-key デフォルトではC-b(Ctrl + b)

## bind-key d : デタッチ(tmuxの終了)

## bind-key c : 新しいウィンドウを作る

## bind-key n : 次のウィンドウへ移動する

## bind-key p : 前のウィンドウへ移動する

## bind-key 数字 : 指定したウィンドウへ移動する

## bind-key w : ウィンドウを一覧表示する

## bind-key % : 画面を縦に分割する

## bind-key ” : 画面を横に分割する

## bind-key ! : 画面の分割を解除する

## bind-key o : 分割した画面間を移動する

## bind-key , : windowに名前をつける

## bind-key ? : コマンド一覧を表示

# bind-key + [pgup pgdn]

Scroll window. \
q \
&nbsp;&nbsp;&nbsp;&nbsp;exit
