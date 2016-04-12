title: "取消自動開啟 Android File Transfer"
date: 2016-04-12 00:36:56
categories:
  - MAC
  - others
tags:
  - MAC
  - Android
---

{% asset_img "android_file_transfer.png" "Android File Transfer" %}

Google 官方推出的 [__Android File Transfer__](https://www.android.com/filetransfer/) 是一款專為 OSX 瀏覽 Android 裝置檔案目錄的軟體
只要 Android 裝置透過 USB 連接 MAC 電腦，就會自行跳出瀏覽檔案目錄的介面

__Download:__
https://www.android.com/filetransfer/

{% asset_img "user_interface.png" "使用者介面" %}


## 無法正常開啟

{% asset_img "cannot_access.png" "can not access" %}

如果連接時，出現以上的警告訊息，請先將 Android 的 USB 選項調整至 `檔案轉移`，再重新開啟 `Android File Transter`

{% asset_img "usb_option.png" "USB 選項" %}

## 關閉自動啟動

只要 Android 一插上 MAC 電腦，就立即跳出 `Android File Transter`，但有時候我們只是想要讓手機插在電腦上充電而已，還要手動關掉也是挺惱人的

其實他是有另外一個背景程序 `Android File Transfer Agent`，他的任務是當發現有 Android 裝置透過 USB 連接電腦時，就啟動 `Android File Transter`；因此只要將 `Android File Transfer Agent` 移除，就不會自行啟動了

<br>

1. ### 關閉背景程序 `Android File Transfer Agent`

  開啟 `活動監視器 (Activity Monitor)` > 找到 `Android File Transfer Agent`後點兩下開啟 > 按 `結束` 終止背景程序

  {% asset_img "activity_monitor.png" "活動監視器" %}

  這時候我們再插拔 USB，`Android File Transfer` 已經不會再自行啟動了

  但是只要一開啟 `Android File Transter`，他就會默默得把 `Android File Transfer Agent` 重新叫起來，因此我們要將 `Android File Transfer Agent` 移除才行

2. ### 移除 `Android File Transfer Agent`

  `Android File Transfer Agent` 檔案位置如下：

  * `/Applications/Android File Transfer.app/Contents/Resources`
  * `~/Library/Application Support/Google/Android File Transfer`

  可以在 `Finder` 按 `cmd + shift + G` 貼上以上位置前往，或是用 `終端機` 都過指令的方式來開啟資料夾

  {% asset_img "file_path_1.png" "/Applications/Android File Transfer.app/Contents/Resources" %}
  {% asset_img "file_path_2.png" "~/Library/Application Support/Google/Android File Transfer" %}

  你可以選擇備份檔案（重新命名），如果未來有需要的時候再把它加回來（把檔案名稱改回來）
  如果你很確定不要這個功能，那就直接刪除吧！

3. ### 將 `Android File Transfer Agent` 從 `登入項目` 中移除

  如果你選擇不移除，而是重新命名的話，下次登入時 `Android File Transfer Agent` 還是會被啟動，因此必須從 `登入項目` 把它移除

  * `系統偏好設定（System Preferences）` > `使用者群組（Users & Groups）` > `登入項目（Login Items）`

  {% asset_img "user_login_items.png" "登入項目" %}


這樣就大功告成啦！

不過這些步驟實在太繁瑣了，我覺得 `Android File Transfer` 應該要內建這個偏好設定才對！
