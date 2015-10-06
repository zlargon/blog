title: "如何刪除 RarGenie"
date: 2015-06-29 22:10:46
categories:
    - MAC
    - 其他
tags:
    - 惡意軟體
    - RarGenie
    - Listchack
---

{% asset_img "MacKeeper.png" "Mac Keeper" %}

最近我發現，只要我的 MAC 一下載 `.rar` 的檔案，就會彈出以下這個視窗，問你要不要試看看 `RarGenie` 啊~

看了就令人非常的惱怒 !!!

{% asset_img "RarGenie.png" "RarGenie" %}

這類的惡意軟體感覺都是出自惡名昭彰 `Mac Keeper`

他們通常都會躲在網頁的廣告裡，或是不知名的軟體安裝裡面，騙使用者去下載安裝

如果有看那個白色的機器人，千萬不要點他啊！

---

然後這一類的惡意軟體最可惡的地方是，當你上網 google 要如何移除 `RarGenie` 的時候，居然會出現一大堆網域名稱為 `www.rargenie.com` 的網站

全部都是教你一些刪不乾淨的方法，一看就知道非常有問題!!!

以下有我自己研究的解決方法

文章的最下方是我在研究問題的一些過程

如果未來又冒出新的惡意軟體，也可以依循同樣的方法解決問題

有興趣的話可以看一下 ^_^

---

# 解決方法

1.打開`活動監視器`把 `AppAS` 強制結束

2.移除 `Listchack.app` (從終端機執行以下指令)

``` bash
$ rm -rf ~/Library/Application\ Support/Listchack
```

3.移除 `Listchack` 相關的 `.plist`

``` bash
$ rm -rf ~/Library/LaunchAgents/Listchack.*.plist
```

---

# 研究過程

我只有在網路上 google 到 Apple 官方提供的移除惡意廣告軟體的文件，不過裡面並沒有提到 `RarGenie`

[Remove unwanted adware that displays pop-up ads and graphics on your Mac](https://support.apple.com/en-us/HT203987)

首先，我經過簡單的測試之後，發現彈出 `RarGenie` 的條件是：當有某個 `.rar` 被新增到 `~/Downloads` 時會觸發

這表示並不是由於從網路下載的這個動作所造成，因此排除是網路或瀏覽器的問題

（只要把某個 `.rar` 的檔案，刪除 -> 還原，就會一直彈出視窗）

從`活動監視器`去觀察所有的程序，發現每次彈出 `RarGenie` 的時候，就會冒出一個 `AppAS` 的程序

按 ___`Don't Use`___ 關掉之後，就會從`活動監視器`中消失

{% asset_img "ActivityMonitor.png" "Activity Monitor" %}

點進去看，就可以查到他的詳細資料

原來他是躲在 `Listchack.app` 底下的某個程式，其父程序為 `launchd`

{% asset_img "AppAS.png" "AppAS" %}

___推論：`launchd` 會去監聽 `~/Downloads` 的檔案變化，如果事件被觸發就會去把 `AppAS` 叫起來___

---

## launchd

我在 google 上找到這位大神的文章，對於 `launchd` 做了非常詳細的說明

[Mac OS X 的 Launch Daemon / Agent](https://blog.yorkxin.org/posts/2011/08/04/osx-launch-daemon-agent/)

___在使用者登入以後，會執行屬於該使用者的 launchd ，負責處理 Launch Agent ，做的事跟上面載入 Launch Daemon 很像，差別在於它從以下的目錄載入 plist：___
* ___`/System/Library/LaunchAgents`___
* ___`/Library/LaunchAgents`___
* ___`~/Library/LaunchAgents`___

___由使用者執行的任何程式也都是 launchd 來執行的，所以 launchd 也是該使用者的所有 processes 之母。___

因此除了要把 `~/Library/Application\ Support` 底下的 `Listchack.app` 移除之外

也要到這三個目錄下去檢查是否有相關的 `.plist`，全部要一併刪除

---

## Listchack

另外我 google 關鍵字 `Listchack` 有找到一篇文章

[Genieo adware proliferating](http://www.thesafemac.com/genieo-adware-proliferating/)

裡面提到，除了之前非常盛行的 `Genieo` 和 `InstallMac` 之外

現在又多了 `GoldenBoy`, `Texiday`，以及最新的 `Listchack`

然後我檢查了一下 `~/Library/Application\ Support/`，我居然也有中 `Texiday`

二話不說，趕緊刪掉!!

---

## Script

另外，由於看 Apple 官方提供的文件，要一個一個手動刪除 malware 實在太累了

因此我寫了一個 shell script，並且放到 Gist

[remove_malware.sh](https://gist.github.com/zlargon/3253fefdde55041a7d5e)

可以自行下載使用 : )
