title: "觸控板設定及 Better Touch Tool"
date: 2015-10-05 03:18:20
categories: MAC
tags:
    - BetterTouchTool
---

{% asset_img "bettertouchtool_icon.png" "Better Touch Tool" %}

# 單指 tap = 滑鼠左鍵，兩指 tap = 滑鼠右鍵

* 系統偏好設定 > 觸控式軌跡板 > 點按 > 勾選 "點一下選按"

* 系統偏好設定 > 觸控式軌跡板 > 點按 > 勾選 "輔助按鈕" > 用兩指按一下或點一下

{% asset_img "touchpad_tap.png" "點一下選按" %}

<br>

# 啟動 tap 拖移功能

__先在觸控板 tap 兩下，第二下手指不離開觸控板，即可開始滑鼠拖曳__

* 系統偏好設定 > 輔助使用 > 左欄找 "滑鼠與觸控式軌跡板" > 觸控式軌跡板選項 > 勾選 "啟用拖移"

{% asset_img "touchpad_drag.png" "啟用拖移" %}

之前的 OSX 預設是三指拖移，可能 Apple 自己也察覺這是一個很爛的設計，在新版的 OSX 已經默默的拿掉這個功能了

<br>

# Better Touch Tool（免費 必裝）

Mac 裡面預設可以修改的觸控手勢非常的少

如果我們希望 Mac 可以支援更多手勢的話，就必須要靠 Better Touch Tool 來輔助

官方網址：http://www.bettertouchtool.net/

他主要支援兩大功能：

* 把觸控板的手勢，對應到指定的滑鼠、按鍵、或其他功能

* 支援透過拖曳視窗的方式，重新調整視窗大小，就像在 windows 一樣

網路上有非常多部落客推薦這款軟體，google 就可以查到很多相關的文章

<br>

# 三指 tap = 滑鼠中鍵（Better Touch Tool）

我們在瀏覽網頁的時候，想要對某超連結從新分頁開啟，可以使用滑鼠中間

或是，我們經常會用滑鼠中鍵，直接關閉網頁分頁

這是一個非常方便的功能，但是 Mac 裡面沒有這樣設定

這時候我們就可以透過 `Better Touch Tool` 來幫助我們實現這個功能

{% asset_img "bettertouchtool_three_finger_tap.png" "三指 tap" %}

要記得到設定裡面勾選 "Launch BetterTouchTool on startup"，這樣每次開機之後他會就自動在背景發功

{% asset_img "bettertouchtool_launch.png" "開機啟動 Better Touch Tool" %}

<br>

# 自動調整大小視窗（Better Touch Tool）

相較於 Mac 視窗紅綠燈失敗的設計，Better Touch Tool 完全解決了調整視窗大小的問題

操作簡單、直覺

1. 把視窗拖曳到螢幕上方，視窗自動放到最大
2. 移到左右兩側，視窗自動縮放大小為螢幕的 1/2
3. 移到螢幕四角，視窗自動縮放大小為螢幕的 1/4

{% asset_img "bettertouchtool_window_snapping.png" "設定 window snapping" %}

<br>

### 示範影片

{% youtube xy4jE1SE4gQ %}
