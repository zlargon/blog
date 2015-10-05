title: "終端機 iTerm2 及設定 bash_profile"
date: 2015-10-05 17:41:52
categories: MAC
tags:
    - iTerm2
---

{% asset_img "iterm2_icon.png" "iTerm2" %}

Mac 原廠提供的終端機，在 10.10 改版之後已經比以前好用很多了

但是說到 Mac 終端機，`iTerm2` 絕對是你最佳的選擇

iTerm2 官方網址：https://www.iterm2.com/

`iTerm2` 最大的特色是，他可以隨時隨地向右、向下新增內分頁

例如說，我現在想要寫完一分 code，準備要用提交

我就可以左邊 `git diff`，右邊寫 commit message

左右對照非常方便

主要操作的快捷鍵如下：

| 快捷鍵 					| 功能 			|
| --- 						| --- 			|
| `⌘ + T` 					| 開新分頁 		|
| `⌘ + 左右`					| 切換分頁 		|
| `⌘ + D` 					| 向右開新內分頁 	|
| `⌘ + shift + D` 			| 向下開新內分頁 	|
| `⌘ + option + 上下左右` 	| 切換內部分頁	|
| `⌘ + W` 					| 關閉所在的分頁 	|
| `⌘ + Q` 					| 關閉 iTerm2	|

<br>

# 設定從所在的目錄開啟新分頁

iTerm2 預設每次開新分頁，都會跑回 `Home` 目錄，這樣會很不方便

iTerm2 可以改成從所在目錄底下，開啟新的分頁

按 `cmd + ,` 進入設定頁面 > `profile` > `General` > `Working Directory` > `Reuse previous session's directory`

{% asset_img "working_directory.png" "從所在的目錄開啟新分頁" %}

<br>

# 設定 `bash_profile`

Mac 終端機預設是沒有顏色區分的，只有白底黑字

對於開發者來說，終端機字體的顏色是非常重要的

如果想要像在 Linux 一樣有顏色的話，就必須自行新增 `~/.bash_profile`

以下是我個人慣用的 `bash_profile`

{% codeblock "~/.bash_profile" lang:bash https://gist.github.com/zlargon/7184ab11631153bdb9f0 gist %}
# enables color in the terminal bash shell
export CLICOLOR=1

# sets up the color scheme for list
export LSCOLORS=ExFxCxDxBxegedabagacad

# enables color for iTerm
export TERM=xterm-color

export TERM="xterm-color"
PS1='\[\e[0;33m\]\u\[\e[0m\]@\[\e[0;32m\]\h\[\e[0m\]:\[\e[0;34m\]\w\[\e[0m\]\$ '

# sets up proper alias commands when called
alias ls='ls -vG'
alias ll='ls -al'
alias la='ls -a'
alias vi='vim'
{% endcodeblock %}

新增完成之後，重開終端機，就會有美麗的顏色了

<br>

# 自訂 iTerm 的背景主題

按 `cmd + ,` 進入設定頁面 > `profile` > `Colors` > `Load Presets...`

建議如果要時間使用終端機的話，選擇暗色系的會比較保護眼睛

我覺得列表中既有的 `Tango Dark` 算是還不錯，顏色看起來很舒服

{% asset_img "iterm_theme.png" "設定 iTerm 背景主題" %}

如果既有的顏色都不滿意的話，也可以到這個網站下載別人做好的背景主題

http://iterm2colorschemes.com/

<br>

# 開啟 `vim` 的語法 highlight

Mac 預設的 `vim` 的語法 highlight 是關閉的

所以要自行新增 `~/.vimrc`

{% codeblock "~/.vimrc" lang:vim %}
syntax on
{% endcodeblock %}
