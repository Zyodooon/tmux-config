# tmux 設定

tmux の設定ファイルを GitHub で管理するためのリポジトリ。

## 置き場所

- 実体: `/home/ponqoo/working/config/tmux`
- tmux が読む場所: `/home/ponqoo/.tmux.conf`
- `/home/ponqoo/.tmux.conf` は `/home/ponqoo/working/config/tmux/tmux.conf` への symlink。
- remote: `git@github.com:Zyodooon/tmux-config.git`

## 変更を書き込む

設定を編集する。

```bash
cd /home/ponqoo/working/config/tmux
nvim tmux.conf
```

変更内容を確認する。

```bash
git status
git diff
```

現在の tmux セッションへ反映する。

```bash
tmux source-file /home/ponqoo/working/config/tmux/tmux.conf
```

GitHub に上げる。

```bash
git add tmux.conf README.md
git commit -m "tmux設定を更新"
git push
```

別マシンで反映する。

```bash
git clone git@github.com:Zyodooon/tmux-config.git /home/ponqoo/working/config/tmux
ln -s /home/ponqoo/working/config/tmux/tmux.conf /home/ponqoo/.tmux.conf
```
