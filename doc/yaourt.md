Yaourt(非公式パッケージマネージャ)の導入
---

`Arch`には`AUR`パッケージと呼ばれる非公式のサードパーティパッケージがあり、
誰でも気軽に登録、公開することができる。

これを手動でインストールするのはそれほど手間ではないものの、
毎回同じような手順を踏むのは億劫なので、
この時点で`yaourt`を導入しておく。

基本的には以下の通りやればOK。

[Yaourt (日本語) - ArchWiki](https://wiki.archlinux.org/index.php/Yaourt_(%E6%97%A5%E6%9C%AC%E8%AA%9E))

## 導入

今回は簡単な方法を選択した。
`/etc/pacman.conf`に以下を追加する。

~~~
[archlinuxfr]
SigLevel = Never
Server = http://repo.archlinux.fr/$arch
~~~

その後、

~~~
# pacman --sync --refresh yaourt
~~~

を実行する。

## 使い方

~~~
$ yaourt -S <AUR名>
~~~

でインストールできる。途中`PKGBUILD`を編集するかなど聞いてくるが
必要なところ(インストールするか？など)以外は基本的にはNoで良い。

注意点として、ユーザ権限を昇格せずに使うこと。
