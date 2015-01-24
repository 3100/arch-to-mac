日本語入力
---

日本語入力には普段慣れ親しんでいる`Google日本語入力`(`mozc`)を利用したい。

今回は導入が簡単そうだという理由で`fcitx`を用いることにした。
(事前に`uim`も試したが、ツールバーがズレたり、知識不足のせいかmozcがうまく動かせなかったりしたので断念した)

[Fcitx (日本語) - ArchWiki](https://wiki.archlinux.org/index.php/Fcitx_(%E6%97%A5%E6%9C%AC%E8%AA%9E))

## 導入

インストールは以下の通り。

~~~
# pacman -S fcitx fcitx-configtool, fcitx-mozc
~~~

尚、`fcitx-configtool`はgtk3ベースのGUI設定ツールなので、環境によっては異なるものを選択すること。

## 設定

`xfec4`は`$HOME/.xprofile`の設定を読み込むのでここに記述した。

~~~
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS='@im=fcitx'
~~~

`/etc/locale.conf`も変えておく(必須かどうかはわかっていない)

~~~
LANG=ja_JP.UTF-8
#LANG=en_US.UTF-8
~~~

XDG互換のデスクトップ環境(`KDE`、`GNOME`、`XFCE`, `LXDE`など)を使っている場合は
再ログインで自動的に`fcitx`が起動されるはず。

### mozcの登録

GUI設定画面を開き、`MOZC`を登録する。
