f.luaみたいなブルーライト対策
---

Linuxには`redshift`という`flux`にインスパイアされたツールがあるみたいだ。

[Redshift - ArchWiki](https://wiki.archlinux.org/index.php/Redshift)

## 導入

一応GUIツールも入れておく。

~~~
# pacman -S redshift redshift-gtk
~~~

## 設定

自動起動したいので、サービスとして登録する。

そのままでは動かなかったので`/usr/lib/systemd/user/redshift.service'に修正を行う。

~~~
[Service]
Environment=DISPLAY=:0
~~~

のように項目を追加。

cf. [[Solved] Redshift fails to run as systemd unit, works in terminal (Page 1) / Newbie Corner / Arch Linux Forums](https://bbs.archlinux.org/viewtopic.php?pid=1417568)

また、`$HOME/.config/redshift.conf`を作成し、緯度経度などを指定する。(ここでは東京の位置を入力)
(`redshift-scheduler`といった代替案もある)

~~~
[redshift]
; Set the day and night screen temperatures
temp-day=5700
temp-night=3500

; Enable/Disable a smooth transition between day and night
; 0 will cause a direct change from day to night screen temperature.
; 1 will gradually increase or decrease the screen temperature
transition=1

; Set the screen brightness. Default is 1.0
;brightness=0.9
; It is also possible to use different settings for day and night since version 1.8.
;brightness-day=0.7
;brightness-night=0.4
; Set the screen gamma (for all colors, or each color channel individually)
gamma=0.8
;gamma=0.8:0.7:0.8

; Set the location-provider: 'geoclue', 'gnome-clock', 'manual'
; type 'redshift -l list' to see possible values
; The location provider settings are in a different section.
location-provider=manual

; Set the adjustment-method: 'randr', 'vidmode'
; type 'redshift -m list' to see all possible values
; 'randr' is the preferred method, 'vidmode' is an older API
; but works in some cases when 'randr' does not.
; The adjustment method settings are in a different section.
adjustment-method=randr

; Configuration of the location-provider:
; type 'redshift -l PROVIDER:help' to see the settings
; e.g. 'redshift -l manual:help'
[manual]
lat=35.7
lon=139.7

; Configuration of the adjustment-method
; type 'redshift -m METHOD:help' to see the settings
; ex: 'redshift -m randr:help'
; In this example, randr is configured to adjust screen 1.
; Note that the numbering starts from 0, so this is actually the second screen.
[randr]
screen=0
~~~

最後に、サービスを自動登録して完了。

~~~
$ systemctl --user enable redshift.service
~~~
