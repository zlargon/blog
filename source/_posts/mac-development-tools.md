title: "推薦的開發工具"
date: 2015-10-06 12:35:21
categories:
    - MAC
    - tools
tags:
    - Xcode
    - iTerm2
    - brew
    - git
    - repo
    - SublimeText
    - TextWrangler
---

由於我之前工作都是用 Mac 在做軟體開發，後來有滿多同事看我用得很順手

後來都想買 Mac 來用看看 XD

我個人非常推薦用 Mac 進行軟體開發工作

像是我之前常常會跑台北參加各種開發者 Conference

不論是演講者或是底下的開發者們，幾乎是人手一台 Mac

Mac 的穩定性實在是令人非常驚豔，我覺得工作上沒什麼比穩定性還要更重要的了！

這篇主要是寫給初次在 Mac 進行開發的人看的

主要介紹是一些推薦的開發套件，以及一些提醒事項

<br>

| 應用程式 			| 簡介 												|
| --- 				| --- 												|
| Xcode 			| 開發 `Mac OSX`、`iOS App` 專用 IDE					|
| iTerm2 			| 神器等級的終端機										|
| brew 				| 安裝其他 `command line`，類似 `Ubuntu` 的 `apt-get`	|
| git 				| 版本控制軟體										|
| repo 				| 版本控制軟體										|
| Sublime Text 		| 神器等級的文字編輯器									|
| TextWrangler 		| 很方便搜尋關鍵字的文字編輯器							|

<br>

{% asset_img "xcode.png" "Xcode" %}

# 1. 安裝 Xcode

建議從 Mac App Store 下載：https://itunes.apple.com/tw/app/xcode/id497799835?l=zh&mt=12

Xcode 是開發者必裝的軟體，包含了 IDE, `Command Line Tools`, `Clang Compiler`, ...

其實如果不想要 IDE 的話，也是可以直接到 Apple 開發者中心，直接下載 `Command Line Tools`

不過這裡是建議直接下載 Xcode，後續透過 Mac App Store 更新會比較方便

<br>

{% asset_img "iterm2.png" "iTerm 2" %}

# 2. 安裝 iTerm 2（★★★★★★）

Mac 神器等級的終端機

請參考這篇：{% link "終端機 iTerm2 及設定 bash_profile" http://zlargon.github.io/blog/2015/10/05/mac-terminal/  %}

內有圖文並茂的設定教學

<br>

# 3. 安裝 Home Brew

官方網站：http://brew.sh/

`brew` 的功能等同於 Ubuntu 上的 `apt-get`

在 `brew` 出現以前有 `MacPorts`，但是由於他的依賴關係做得不好，常常令人頭痛

於是 `brew` 就出現了拯救了大家，後來就變成 Mac 上的主流

安裝很簡單，只需要執行以下的 command line 即可

{% codeblock lang:bash %}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endcodeblock %}

Mac 原廠設定有包含 Ruby, Python ... 等大多數的開發套件，所以可以直接執行指令

<br>

{% asset_img "git.png" "Git" %}

# 4. 安裝 git

官方網站：https://git-scm.com/

現今主流的版本控制軟體，應該不用多作解釋吧 XD

可以透過官方網站的 `.dmg` 來安裝，也可以透過 `brew` 來安裝

{% codeblock lang:bash %}
brew install git
{% endcodeblock %}

<br>

### Mac File System 不分大小寫

Linux 的 File System 會區分大小寫不同的檔案

而 Mac 與 Windows 一樣，會將大小寫不同的檔案，視為同一個檔案

之前有遇過 A 使用 Linux 平台開發，新增檔案 a123 跟 A123

結果導致我在 Mac 要同步檔案的時候，發生錯誤，還弄了老半天

所以這一定要特別注意

<br>

### git 在各平台的指令，會有些微的不同

例如說，在 Mac 要將檔案加入提交的時候

已刪除的檔案，可以用 `git add <removed_file>`

但是在 Linux 上，必須要用 `git rm <removed_file>` 才能加入

就只是要提醒，各平台的 git 指令會有一點點些微的不同

<br>

{% asset_img "gerrit.png" "Gerrit Code Review" %}

# 5. 安裝 repo（搭配 Gerrit 使用）

repo 官方網站：https://code.google.com/p/git-repo/

官方下載安裝教學：http://source.android.com/source/downloading.html#installing-repo

Google 為管理 Android 這種超大型的專案，於是基於 Git Server 開發出了 [Gerrit](https://www.gerritcodereview.com/) 系統

可以有效率的將一個大專案拆成各個小專案，捨棄 git submodules，統一使用 manifest.xml 來管理

可以減少很多不必要的 patch，例如 merge branch, commit, update submodules commit, ... 等等

開發者可以更專注於功能的開發，追縱 bug

其 Code Review Web 介面，可以透過 `Change-Id` 追蹤每個 `patch` 的訂正情形

<br>

`Repo` 是搭配 `Gerrit` 所誕生的工具，作為 `client` 端的 `command line`

目前最新版的 `repo` 是使用 `python` 寫的，由於 Mac 內建已經有安裝 `python 2.7.10` 所以可以直接執行

（如果要在 `Windows` 執行 `repo`，必須要另外安裝 `python` 才能運行）

以 `git` 的指令為基礎，封裝了 `git` 與 `Gerrit Server` 複雜的設定以及溝通的指令

例如 `git pull`, `git push`, `git fetch` 等容易出錯，及設定錯誤的指令

大部份的時候，只需要透過 `repo sync`, `repo upload` 即可完成同步、上傳程式碼

執行以下 `command line` 即可將 `repo` 安裝到 `~/bin` 底下：

{% codeblock lang:bash %}
mkdir -p ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
{% endcodeblock %}

新增路徑 `~/bin` 到 `bash_profile`

{% codeblock ~/.bash_profile lang:bash %}
export PATH=$PATH:~/bin
{% endcodeblock %}

<br>

使用 `repo sync` 指令時，他會去先下載 repo 一份最新的 source code，放到 `.repo/` 目錄底下

他透過 `GPG` 去驗證 repo tag 的版本

如果在 Mac 上使用 `repo` 發生 `GPG` 相關的錯誤訊息，請安裝 `GPG Tools`

{% asset_img "gpg.png" "GPG Tools" %}

官方網站：https://gpgtools.org/

安裝好之後，他會要求你輸入信箱等等資訊，不用填，直接關掉就可以了

<br>

{% asset_img "sublime_text.jpg" "Sublime Text 3" %}

# 6. Sublime Text 3（★★★★★★）

官方網站：http://www.sublimetext.com/3

文字編輯超級神器，應該不用多作解釋吧 XD

<br>

### 設定 Sublime Command Line

https://www.sublimetext.com/docs/2/osx_command_line.html

可以直接透過 command line 用 sublime 開啟檔案

<br>

### 安裝 Package Control

https://packagecontrol.io/installation#st3

Sublime Text 有提供各式各樣的套件，可以很簡單的擴充

例如，我個人經常會使用 Markdown 語法來編寫文件、寫網誌，就非常推薦套件 ___MarkdownLight___

作者的 github：https://github.com/sekogan/MarkdownLight

而 ___Babel___ 也有開發 sublime 的套件，可同時支援 ES5, ES6, JSX 的語法

Babel 官方網址：https://babeljs.io/

Babel Github：https://github.com/babel/babel-sublime

<br>

{% asset_img "text_wrangler.png" "TextWrangler" %}

# 7. TextWrangler（★★★）

官方網站：http://www.barebones.com/products/textwrangler/

建議從 Mac App Store 安裝：https://itunes.apple.com/tw/app/textwrangler/id404010395?mt=12

其實他是一個文字編輯器

他對我來說 TextWrangler 最大的賣點是，他文內搜尋的介面做得很好

在 debug 的時候，很適合在幾萬行的 log 裡面搜尋關鍵字

___然而一份 log 會有幾萬行，這件事本身很可能就是一個 bug___
