title: "Mac 攝影機無法連接"
date: 2017-03-22 05:01:16
categories:
    - MAC
    - others
tags:
    - Camera
    - iSight
---

{% asset_img "there_is_no_connected_camera.jpg" "攝影機無法連接" %}

我最近發現我的 Mac (OS X 10.11.6) 有時候攝影機會突然無法正常開啟
即使我已經將所有可能會使用攝影機的應用程式都關掉了，但是攝影機依然無法運行
直到我重開機之後，才會恢復正常

後來我在 YouTube 找到了這個影片，才解決了我的問題
{% youtube P-6kTfqn-b8 %}

<br>

## 解決方案

在終端機輸入指令（注意英文大小寫）

``` bash
sudo killall VDCAssistant
```

`VDCAssistant`這個程序負責背景執行 Mac 的攝影機（iSight）
使用這個指令後，會把背景執行的`VDCAssistant`強制關掉，接著再次重新啟動

{% asset_img "VDCAssistant.png" "VDCAssistant (點擊放大)" %}

這個指令必須要給予`管理員權限`，因此要在前面加上`sudo`，並且輸入密碼
否則他會顯示 `No matching processes belonging to you were found`
如果沒設定過密碼的話，請直接按 `Enter`

__Note:__
影片中有附著，若上述指令無法作用的話，請改用以下指令

``` bash
sudo killall AppleCameraAssistant
```

<br>

## 指令介紹

`sudo` - 使用管理員權限
`killall <PROCESS_NAME>` - Kill All 顧名思義，砍掉所有名稱為 `<PROCESS_NAME>` 的程序

## 參考連結

* https://youtu.be/P-6kTfqn-b8
