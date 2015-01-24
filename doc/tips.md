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
