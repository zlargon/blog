title: "中文輸入法選字框 無法顯示"
date: 2016-06-24 09:07:10
categories:
    - MAC
    - others 
tags:
    - 中文輸入法
---

{% asset_img "osx_logo.jpg" "OS X" %}

自從我的 MAC OSX 升級到 10.11 之後，就常常會遇到中文輸入法選字框消失的情形
只能靠重開機來修復，還滿煩的

我後來有拍影片傳到 Youtube，也有在 Apple 社群發問，終於遇到好心人回覆了
ya~ 終於不用再一直重開機了 ^0^

## 解決方案

在終端機輸入 `killall TCIM`

{% asset_img "TCIM.png" "TCIM" %}

這個指令把背景執行的`TCIM`（中文輸入法）的程序關掉
當作業系統發現 `TCIM` 不見之後，就會強迫重新啟動 `TCIM`，這時候選字框就回來了

## 影片連結

{% youtube m_f44XGfDXw %}

<br>

## 參考連結

* http://blog.tenyi.com/2015/10/mac-os-x-ei-capitan.html
* https://discussionschinese.apple.com/thread/73381
