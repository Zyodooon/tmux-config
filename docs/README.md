# tmux コマンド・操作ガイド

このリポジトリの tmux 設定では、通常のプレフィックスキーを `Ctrl-q` に変更している。
以下では、`Prefix` は `Ctrl-q` を意味する。

`Ctrl-b` を使う設定は `../tmux-ctrl-b.conf` にある。必要な場合は、リポジトリ直下の `README.md` を参照する。

## 最初に覚える操作

まずは次の操作を覚えると使いやすい。

1. `tmux new -s work` で作業セッションを作る。
2. `Prefix |` または `Prefix -` で画面を分割する。
3. `Ctrl-h/j/k/l` でペインを移動する。
4. `Prefix [` でコピーモードに入り、`Space` で選択を開始する。
5. `y` で選択範囲をコピーし、`q` または `Esc` で終了する。
6. `Prefix d` でセッションから抜ける。
7. `tmux attach -t work` で作業を再開する。

## セッション

### 新しいセッションを作る

```bash
tmux new -s work
```

### セッション一覧を見る

```bash
tmux ls
```

### 既存セッションに接続する

```bash
tmux attach -t work
```

短縮形も使える。

```bash
tmux a -t work
```

### セッションから抜ける

tmux自体を終了せず、セッションを残したまま抜ける。

```text
Prefix d
```

つまり `Ctrl-q` を押してから `d` を押す。

### セッションを終了する

```bash
tmux kill-session -t work
```

## ウィンドウ

ウィンドウは、1つのセッション内にあるタブのようなもの。

| 操作 | キー |
| --- | --- |
| 新しいウィンドウ | `Prefix c` |
| 次のウィンドウ | `Prefix n` |
| 前のウィンドウ | `Prefix p` |
| ウィンドウ番号を指定 | `Prefix 0` ～ `Prefix 9` |
| ウィンドウ名を変更 | `Prefix ,` |
| ウィンドウ一覧 | `Prefix w` |
| ウィンドウを閉じる | `Prefix &` |

コマンドからウィンドウを作ることもできる。

```bash
tmux new-window -t work -n editor
```

## ペイン

ペインは、1つのウィンドウを分割した画面。

この設定では、ペイン分割のキーを変更している。

| 操作 | キー |
| --- | --- |
| 左右に分割 | `Prefix |` |
| 上下に分割 | `Prefix -` |
| 左のペインへ移動 | `Ctrl-h` |
| 下のペインへ移動 | `Ctrl-j` |
| 上のペインへ移動 | `Ctrl-k` |
| 右のペインへ移動 | `Ctrl-l` |
| ペインを閉じる | `Prefix x` |
| ペインを最大化・元に戻す | `Prefix z` |
| ペインの番号を表示 | `Prefix q` |
| ペインを入れ替える | `Prefix o` |

`Ctrl-h/j/k/l` はプレフィックスキーを押さずに使える。

## コピー・スクロール

マウス操作が有効になっているため、マウスホイールでスクロールできる。

### コピーモードに入る

```text
Prefix [
```

コピーモード中はvi風のキー操作が使える。

| 操作 | キー |
| --- | --- |
| 上下移動 | `j` / `k` |
| ページ送り | `Ctrl-f` / `Ctrl-b` |
| 選択開始 | `Space` |
| 選択範囲をコピー | `y` |
| コピーモード終了 | `q` または `Esc` |

`y` または `Ctrl-Shift-c` で選択範囲をクリップボードへコピーする。

## 設定を再読み込みする

現在の設定を変更したあと、tmuxを終了せずに反映できる。

```bash
tmux source-file "$HOME/.tmux.conf"
```

または、tmux内で次のキーを押す。

```text
Prefix :
source-file ~/.tmux.conf
Enter
```

## 設定ファイルを指定して起動する

現在の設定を変更せずに、Ctrl-b版を試す場合:

```bash
CONFIG_ROOT="$HOME/working/config"
tmux -f "$CONFIG_ROOT/tmux/tmux-ctrl-b.conf" new -s ctrl-b-test
```

## よく使うコマンド

```bash
# セッション一覧
tmux ls

# セッションへ接続
tmux attach -t work

# セッションを作成して名前を付ける
tmux new -s work

# セッション名を変更
tmux rename-session -t work work2

# セッション内のウィンドウ一覧
tmux list-windows -t work

# セッション内のペイン一覧
tmux list-panes -t work

# tmuxサーバーを終了し、全セッションを閉じる
tmux kill-server
```
