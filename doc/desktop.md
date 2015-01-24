デスクトップ環境の構築
---

見た目的には`GNOME`が洗練されている気がしたが、軽量だと噂の`Xfce`を試した。
実は`Awesome`も少し触ったりしたが、今のところ`Xfce`のほうが素直だと感じている。

[Xfce (日本語) - ArchWiki](https://wiki.archlinux.org/index.php/Xfce_(%E6%97%A5%E6%9C%AC%E8%AA%9E))

## 準備

`Arch`の導入時点でビデオドライバーの導入と、`xorg`関連の導入が済んでいること。

## 導入

関連するツールごとグループでインストールした。

~~~
# pacman -S xfce4
~~~

### ディスプレイマネージャ

起動にはディスプレイマネージャを用いる。`GDM`でも何も問題はないのだが、ざっと調べて`LXDM`にしてみた。
デフォルトの外観(`Industrial`テーマ)は洗練されていない。

~~~
# pacman -S lxdm
~~~

かわりに`yaourt`で導入できる`lxdm-git`には`Arch`向けのテーマが2つ入っている。

~~~
$ yaourt -S lxdm-git
~~~

`lxdm-git`では`/etc/lxdm/lxdm.conf`の`theme`を

* ArchStripes
* ArchDark

に変更できる。(テーマファイル自体は`/usr/share/lxdm/themes`にある)
ついでに見た目をスッキリさせるため、以下の項目も変更した。

~~~
## if show bottom pane
bottom_pane=0

## if show language select control
lang=0
~~~

いずれの場合も、デフォルトセッションを明示しておく。
`/etc/lxdm/lxdm.conf`内で以下のように設定する。
(上の設定をする際に、これを行わないとログインできなくなる)

~~~
[base]
session=/usr/bin/startxfce4
~~~

### ディスプレイマネージャでログインできなくなったら

`CTRL` + `ALT` + `F3`でコンソールログインができる。
そちらでログインし、原因を調査すると良い。
