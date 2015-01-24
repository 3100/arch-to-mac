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

起動にはディスプレイマネージャを用いる。`GDM`でも何も問題はないのだが、ざっと調べて`LXDM`にしてみた。
デフォルトの外観は洗練されていない。

~~~
# pacman -S lxdm
~~~

デフォルトセッションを明示したければ
[LXDM (日本語) - ArchWiki](https://wiki.archlinux.org/index.php/LXDM_(%E6%97%A5%E6%9C%AC%E8%AA%9E))
を参考に`/etc/lxdm/lxdm.conf`を編集する。今回は特に手を付けていない。
