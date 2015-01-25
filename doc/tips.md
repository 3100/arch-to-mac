ちょっとした改善など
---

## caps lockと左ctrlキーの入れ替え

`$HOME/.Xmodmap`といったファイルを作成し、以下のように記述する。

~~~
remove Lock = Caps_Lock
keysym Caps_Lock = Control_L
add Control = Control_L
~~~

`xmodmap`を実行する。

~~~
$ xmodmap $HOME/.Xmodmap
~~~

尚、`GDM`、`XDM`、`KDM`では起動時に`$HOME/.Xmodemap`を自動的に読んでくれるようです。
特に指定していないけど有効なので、`LXDM`でも同じかな？

## タッチパッドの縦スクロールをOS X風にする

natural scrollとか呼ぶらしいです。

上のケースと同様に、`xmodmap`の出番です。
設定ファイルに以下のように追加します。

~~~
pointer = 1 2 3 5 4 7 6 8 9 10 11 12
~~~
## 特定のWebページでFirefoxが汚いフォントを表示する

システムフォントやFirefoxのデフォルトフォントを変更しても解決しない場合
ビットマップフォントが原因の可能性がある。

Xでビットマップフォントを無効にすると解決した。

~~~
$ ln -s /etc/fonts/conf.avail/70-no-bitmaps.conf /etc/fonts/conf.d/
~~~

cf. [Firefox (日本語) - ArchWiki](https://wiki.archlinux.org/index.php/Firefox_(%E6%97%A5%E6%9C%AC%E8%AA%9E)#.E7.89.B9.E5.AE.9A.E3.81.AE.E3.82.A6.E3.82.A7.E3.83.96.E3.83.9A.E3.83.BC.E3.82.B8.E3.81.A7_Firefox_.E3.81.8C.E6.B1.9A.E3.81.84.E3.83.95.E3.82.A9.E3.83.B3.E3.83.88.E3.82.92.E8.A1.A8.E7.A4.BA.E3.81.99.E3.82.8B)
