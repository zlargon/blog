title: "iPhone 相簿照片無法刪除"
date: 2015-10-06 21:14:06
categories:
    - iOS
    - 其他
tags:
    - iTunes
    - iPhoto
---

{% asset_img "iPhoto.png" "iPhoto" %}

在 iPhone 裡面有某些相簿的照片是無法直接刪除的

當我們點進去這些照片時，除了 `"編輯"` 和 `"分享"` 之外，根本找不到 `"刪除"`

這個問題困惑了很多人，其中也包括過去的我

{% asset_img "undeletable.png" "照片無法刪除" %}

這些無法刪除的照片，可以分為兩類，刪除的方式不同：

* __照片串流__：可以直接從 iPhone 刪除
* __事件相簿__：iPhone 必須連接電腦，從電腦刪除

---

# 1. 刪除「照片串流」

開啟 iPhone 設定 > 點選 `iCloud` > 點選 `iPhoto` > 關閉`「照片串流」`

{% asset_img "remove_stream_photo.png" "刪除「照片串流」" %}

<br>

# 2. 刪除「事件相簿」

1. 完全關閉 iPhone`「相簿 App」`

2. 將 iPhone 連接至你的 Mac，並且開啟 `iTunes`

3. 點選 `iTunes` 左上角的 `"裝置圖示"` > 點選左邊的 `"照片"` 欄位

4. 勾選 `"同步照片"`，拷貝照片來自 `"iPhoto"`

5. 勾選 `"所選的照片、事件和面孔並自動包含"`，選擇 `"沒有事件"`

6. 套用設定

{% asset_img "remove_event_albums.png" "刪除「事件相簿」" %}
