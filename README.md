# tmux 設定

tmux の設定ファイルを GitHub で管理するためのリポジトリ。

## 置き場所

- 実体: `<config-root>/tmux`
- tmux が読む場所: `$HOME/.tmux.conf`
- `$HOME/.tmux.conf` を `<config-root>/tmux/tmux.conf` への symlink にすると、標準パスのままこの設定を使える。

例:

```bash
CONFIG_ROOT="$HOME/working/config"
ln -s "$CONFIG_ROOT/tmux/tmux.conf" "$HOME/.tmux.conf"
```

## 変更を書き込む

設定を編集する。

```bash
cd "$CONFIG_ROOT/tmux"
nvim tmux.conf
```

変更内容を確認する。

```bash
git status
git diff
```

現在の tmux セッションへ反映する。

```bash
tmux source-file "$CONFIG_ROOT/tmux/tmux.conf"
```

GitHub に上げる。

```bash
git add tmux.conf README.md
git commit -m "tmux設定を更新"
git push
```

別マシンで反映する。

```bash
CONFIG_ROOT="$HOME/working/config"
git clone <repository-url> "$CONFIG_ROOT/tmux"
ln -s "$CONFIG_ROOT/tmux/tmux.conf" "$HOME/.tmux.conf"
```
