title: "自訂鍵盤及 Karabiner"
date: 2015-10-05 13:22:20
categories: MAC
tags:
    - Karabiner
---

{% asset_img "karabiner.png" "karabiner" %}

# 按住 Fn 時啟用特殊功能鍵

在 Mac 中的按鍵 F1 ~ F12 預設是特殊功能鍵，可以調整螢幕亮度 or 音量

但是如果有些應用程式會很經常按 F1 ~ F12 的按鍵的話，就必須要按著 Fn + F1 ~ F12

例如說，我在虛擬機執行 Windows 或 Linux 的時候，就會經常使用到 F1 ~ F12 等標準功能鍵

所以我會把他的預設改成，按住 Fn 的時候，才會變成特殊功能鍵

* 系統偏好設定 > 鍵盤 > 勾選 "使用所有 F1、F2 等按鍵作為標準功能鍵"

{% asset_img "fn_button.png" "按住 Fn 時啟用特殊功能鍵" %}

<br>

# Karabiner（免費）

一般 Mac 裡面可以自訂的鍵盤按鍵，就只有 Caps Lock, Control, Option, Command 四個按鍵

{% asset_img "default_keyboard_setting.png" "預設可以自訂的按鍵" %}

如果想要自訂其他按鍵的話，可以透過 `Karabiner` 來幫忙

官方網址：https://pqrs.org/osx/karabiner/

原名為 `KeyRemap4MacBook`

網路上也有很多部落客撰寫關於此的文章，可以 google 關鍵字 `Karabiner` 或 `KeyRemap4MacBook`

<br>

# 調換左側的 control 與 command 鍵

由於以前在 PC 上，非常習慣 control 鍵的位置，而且 command 跟 shift 時常要一起按

他們隔得太遠了，很不好按

假如我使用 Mac 的系統設定來修改按鍵的話，右側的 command 也會變成 control

為了保留右側的 command，就可以透過 `Karabiner` 來設定

`Karabiner` 裡面有很多預設的項目，我們只要找到符合我們要的功能打勾就行了

* 展開 `Change Command_L Key (Left Command)` > 勾選 `Command_L to Control_L`
* 展開 `Change Control_L Key (Left Control)` > 勾選 `Control_L to Command_L`

{% asset_img "karabiner_left_ctrl_cmd.png" "調換左側的 control 與 command 鍵" %}

<br>

# 自訂 `del` 鍵

由於 Mac 上只有 `delete` 鍵，等同於 PC 鍵盤的 `Backspace` 鍵，向前刪除文字

如果想要向後刪除文字的話，就要按 `fn + delete`

由於我已經非常習慣使用 `del` 鍵了，所以會希望有一個 `del` 鍵可以用

剛好 `Karabiner` 就已經有提供了這個功能

* 展開 `Change Backslash(\) key` > 勾選 `Backslash(\) to Forward Delete`

由於反斜線通常比較少使用，所以就把它換成 del 鍵，如果想要打反斜線的時候在按著 Fn

{% asset_img "backslash_to_forward_delete.png" "自訂 del 鍵" %}

<br>

# 自訂滑鼠左鍵：為了快速框選大範圍的內容

通常在 PC 上，我們想要一次拖拉框選大範圍的內容時，就只要用按著滑鼠左鍵，然後搭配滑鼠滾球往下拉就行了

但是 Mac 的觸控板沒有滾球，這樣慢慢拖拉好辛苦

所以我會希望鍵盤上能夠有一個特殊的組合鍵，能夠代表滑鼠的左鍵

我只要按住這個特殊的組合鍵，然後兩指在觸控板往上下滑，就可以快速框選大範圍的內容

由於這是我個人獨特的需求，`Karabiner` 預設的列表沒有相似的功能

不過沒關係，`Karabiner` 有提供可以讓使用者新增選項的方法：

* 開啟 `Misc & Uninstall` > `Custom Setting` > `Open private.xml`

{% asset_img "private_xml.png" "private.xml" %}

`private.xml` 可以讓使用者客製化自己的選項

官方文件：https://pqrs.org/osx/karabiner/xml.html.en

所以我決定將 fn + command 設定為滑鼠左鍵

{% codeblock private.xml lang:xml https://gist.github.com/zlargon/16c2927ef9dcf4e3869e gist %}
<?xml version="1.0"?>
<root>
  <item>
    <name>Fn + Cmd to LeftClick</name>
    <identifier>private.fn2leftclick</identifier>
    <autogen>__KeyToPointingButton__ KeyCode::FN, ModifierFlag::COMMAND_L, PointingButton::LEFT</autogen>
  </item>
</root>
{% endcodeblock %}

<br>

* 存檔之後，回到 `Change Key` 頁面，按下 `Reload XML`，自訂的選項就會出現在列表了

{% asset_img "reload_xml.png" "reload xml" %}
