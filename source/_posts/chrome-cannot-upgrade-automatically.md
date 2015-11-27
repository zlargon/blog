title: "Chrome 自動更新永遠失敗"
date: 2015-11-27 20:22:48
categories:
    - MAC
    - others
tags:
    - Chrome
---

{% asset_img "chrome.png" "Chrome" %}

前一陣子有發現 Chrome 瀏覽器的版本總是停留在舊的 43 版

然後打開 `關於 Google Chrome` 的頁面，也無法手動更新

我按照 Chrome 官方的文件步驟，也無法解決問題

[修正 Chrome 更新問題與更新失敗問題](https://support.google.com/chrome/answer/111996?hl=zh-Hant)

我的 Mac 並沒有存在惡意軟體，重開 Chrome、重開電腦也沒用

最後只能重新下載安裝 Chrome，強制更新到最新的 44 版

{% asset_img "about_chrome.png" "關於 Google Chrome" %}

<br>

但是過了一陣子，又突然發現 Chrome 遲遲停留在 44 版，但卻沒有更新到 46 版

後來我上網終於找到了一個可行的解決方案

http://iphone4.tw/forums/showthread.php?t=125277

其作法是將 `GoogleSoftwareUpdate` 刪除，然後迫使 Google Chrome 重新安裝 `GoogleSoftwareUpdate`

這裡要注意的是，新版的 Google Chrome 已經將檔案 `install.py` 改名為 `ksinstall`

{% asset_img "ksinstall.png" "ksinstall" %}

<br>

# 解決方法

* 開啟終端機，執行以下的指令（會分別刪除 ___使用者目錄___ 及 ___根目錄___ 底下 `GoogleSoftwareUpdate`）
* 接著再重開 Chrome 就可以正常自動更新了

{% codeblock lang:bash %}
sudo ~/Library/Google/GoogleSoftwareUpdate/GoogleSoftwareUpdate.bundle/Contents/Resources/ksinstall --uninstall
sudo /Library/Google/GoogleSoftwareUpdate/GoogleSoftwareUpdate.bundle/Contents/Resources/ksinstall --uninstall
sudo rm -rf ~/Library/Google/GoogleSoftwareUpdate
sudo rm -rf /Library/Google/GoogleSoftwareUpdate
{% endcodeblock %}
