title: "Mac 同時收錄 電腦音源 + 麥克風音源"
date: 2016-08-19 00:45:48
categories:
	- MAC
	- tools
tags:
	- Quick Time
	- Soundflower
	- LadioCast
---

{% asset_img "sound_flower.png" "Soundflower" %}

有時候我們想要錄製一些影片，除了自己麥克風的聲音之外，還想要同時收錄一些當時電腦發出的聲音

但是我們在用 Quick Time 錄影時，只能選擇一種音源輸入，而不能同時選擇兩者

因此我們要做就是，把 "麥克風音源" 和 "電腦音源" 混合成單一個音源，然後再導入 Quick Time


# 安裝軟體（Free）

| 名稱 										| 說明 |
| --- 										| --- |
| __Quick Time__ 							| Mac 內建影音播放 / 錄音 / 錄影軟體|
| [__Sound Flower（2.0b2）__][sound_flower] 	| 提供兩個虛擬音源（`2ch`、`64ch`）|
| [__Ladio Cast__][ladio_cast] 				| 可將不同的音源混合輸出 |

> Note:
> 網路上很多 `Sound Flower` 的版本已經過舊，在最新的 Mac 作業系統會無法運行，所以務必要到這裡提供的連結處下載最新版的 `Sound Flower`
> https://github.com/mattingalls/Soundflower/releases

# 流程大綱

1. 從內部 Mac 設定，將 `電腦音源` 導入虛擬音源 `Sound Flower (64ch)`
2. 使用 Ladio Cast 進行混音，將 `麥克風` 和 `64ch` 都導入 `2ch`
3. 在 Quick Time 錄音 / 錄影時，音源選擇虛擬音源 `Sound Flower (2ch)`

{% asset_img "flow.png" "流程圖" %}

# 設定步驟

安裝好 Sound Flower 後，電腦就會出現 `Sound Flower (64ch)` 跟 `Sound Flower (2ch)` 兩個虛擬音源；除此之外，桌面上方的工具列，也會出現 Sound Flower 的圖示。

## 1. 將 Mac `音源輸出` 導入 `Sound Flower (64ch)`

開啟 Mac `系統偏好設定` > `聲音` > `輸出`，選擇輸出裝置 `Sound Flower (64ch)`

{% asset_img "audio_preference.png" "聲音設定" %}

{% asset_img "audio_preference_output_64ch.png" "設定虛擬音源 64 ch" %}

此後虛擬音源 `64ch` 就等同於是 `電腦音源`

> Note:
> 記得要把聲音調到最大，否則錄到的聲音會很小聲

## 2. 設定 Sound Flower

開啟桌面上方工具列的 Sound Flower 圖示，將 `2ch` 設為 `None (OFF)`，將 64ch 設為 `Built-in Output`。

{% asset_img "soundflower_setting.png" "設定 Sound Flower" %}

## 3. 設定 Ladio Cast

使用 Ladio Cast 進行混音，將 `麥克風`、`64ch` 都導入 `2ch`

- 將 `Input 1` 設為 `Built-in Microphone`（麥克風音源）
- 將 `Input 2` 設為 `Sound Flower (64ch)`
- 將 `Main Output` 設為 `Sound Flower (2ch)`

{% asset_img "ladiocast_setting.png" "設定 Ladio Cast" %}

## 4. 設定 Quick Time 音源為 `Sound Flower (2ch)`

最後，只要將 Quick Time 或是其他錄音軟體的音源，設為 `Sound Flower (2ch)` 就大功告成了

{% asset_img "quicktime_input_audio.png" "設定 Quick Time 音源" %}

> Note:
> 平常沒有要錄音的時候，記得將 "第一步驟" 的音源輸出設回原本的預設設定 (`內建揚聲器`or`耳機`)，否則電腦會沒有聲音

# 參考連結

- https://youtu.be/lB9Ovqk5H5c
- http://k-tsubo.com/mac/4582/


[sound_flower]: https://github.com/mattingalls/Soundflower/releases
[ladio_cast]: https://itunes.apple.com/tw/app/ladiocast/id411213048
