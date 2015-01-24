WiFiの設定
---

自動接続に色々手間取ったが、凡ミス(`wpa_actiond`が入っていなかった)だった。
普通にやれば難しくなさそう。

## 導入

~~~
# pacman -S wireless_tools wpa_supplicant wpa_actiond dialog
~~~

## 設定

`netctl-auto`はプロファイルのあるアクセスポイント圏内で自動的に接続を行ってくれる。
このサービスを自動起動に設定する。

~~~
# systemctl enable netctl-auto@wlp2s0b1
~~~

DHCPを利用する場合

~~~
# systemctl enable dhcpcd@wlp2s0b1
~~~

も設定しておく。


### プロファイルの取得

アクセスポイントのプロファイルは
手動接続コマンド`wifi-menu`(`netctl`内にある)に`-o`オプションを付けることで
`/etc/netctl/`下に自動生成してくれる。

~~~
# wifi-menu -o
~~~

でアクセスポイントを指定、キーを入力する。

## トラブルシューティング

もし接続がうまく行かない場合は`systemctl status netctl-auto@wlp2s0b1.service`や`journalctl -xe`などで原因を調べる。

他のネットワークサービスと競合するので、繋がらないからと色々ツールを入れないこと。

また、すでに接続が立ち上がっている(そしてエラーなどでどことも繋がっていない)可能性もある。

~~~
# ip link set down wlp2s0b1
~~~

としたあとに`wifi-menu`あるいは`netctl start <プロファイル名>`で手動接続を試みるなどする。
