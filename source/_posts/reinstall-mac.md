title: "Mac Reinstallation Note"
date: 2018-04-12 12:05:43
categories:
	- MAC
	- others
tags:
	- MAC
---

<br>

{% asset_img "macos.png" "macOS" %}

## 1. Mac Reinstall ([document](https://support.apple.com/en-us/HT204904))

(1) __Restart Mac and press `Shift + Option + Cmd + R`.__
Install the macOS that came with your Mac, or the version closest to it that is still available.

(2) __Use `Dick Utility` to erase the disk.__
{% asset_img "recovery/disk_utilities.jpg" %}

Complete the fields:
- Name: `Macintosh HD`
- Format: `Mac OS Extended (Journaled)` (Don't choose `APFS`)
- Scheme (if available): `GUID Partition Map`

{% asset_img "recovery/erase-disk.png" %}

> Note: If I choose `APFS` as the format, it would always fails to reinstall the macOS. So, I recommand to use `Mac OS Extended (Journaled)` instead.

(3) __Reinstall macOS__
{% asset_img "recovery/reinstall.jpg" %}

## 2. iTerm2 ([download](https://www.iterm2.com/downloads.html))

(1) __Reuse Session's Directory__
{% asset_img "iterm/reuse-session-directory.png" %}

(2) __Color Theme__: `Tango Dark`
{% asset_img "iterm/theme-tango-dark.png" %}

## 3. .bash_profile

{% codeblock "~/.bash_profile" lang:bash %}
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
alias ptt='ssh bbsu@ptt.cc'
 
# mkdir + cd
function mkcd {
  if [ ! -n "$1" ]; then
    echo "Enter a directory name"
  elif [ -d $1 ]; then
    echo "\`$1' already exists"
  else
    mkdir $1 && cd $1
  fi
}
 
# [macOS] Show/Hide the hidden files in Finder.
# add this function to '~/.bash_profile' and reopen terminal.
# Usage: show-file                          -> show
#        show-file 0 / off / hide / false   -> hide
function show-file () {
    opt=$(echo $1 | tr '[:upper:]' '[:lower:]')    # transfer into lowercase
 
    # Hide Files
    if [ "$opt" = "off" ] || [ "$opt" = "0" ] || [ "$opt" = "false" ] || [ "$opt" = "hide" ] ; then
        echo "Hide all the hidden files in Finder."
        defaults write com.apple.finder AppleShowAllFiles FALSE
        killall Finder
        return
    fi
 
    # Show all the Files
    echo "Show all the hidden files in Finder."
    defaults write com.apple.finder AppleShowAllFiles TRUE
    killall Finder
    echo "Use 'show-file off' to hide the hidden files in Finder."
}
{% endcodeblock %}

## 4. vim

Download color theme [Gruvbox](https://raw.githubusercontent.com/morhetz/gruvbox/master/colors/gruvbox.vim) to `~/.vim/colors/gruvbox.vim` and edit `~/.vimrc`:
{% codeblock "~/.vimrc" lang:vim %}
syntax on
set t_Co=256
colorscheme gruvbox
{% endcodeblock %}

## 5. BetterTouchTool ([download](https://folivora.ai/downloads))

(1) launch BetterTouchTool on startup
{% asset_img "bettertouchtool/launch.png" %}

(2) Window Snapping
{% asset_img "bettertouchtool/window_snapping.png" %}

(3) Three Finger Tap = Mouse Middle Click
{% asset_img "bettertouchtool/three_finger_tap.png" %}

(4) Setup shortcut

{% asset_img "bettertouchtool/setup_shortcut.png" %}

## 6. Trackpad

{% asset_img "trackpad/1.png" %}<br>
{% asset_img "trackpad/2.png" %}<br>
{% asset_img "trackpad/3.png" %}

## 7. Enable Dragging

{% asset_img "dragging/1.png" %}<br>
{% asset_img "dragging/2.png" %}<br>
{% asset_img "dragging/3.png" %}

## 8. Enable Function Key for F1 ~ F12

{% asset_img "keyboard/function_key.png" %}

## 9. Karabiner-Element ([download](https://pqrs.org/osx/karabiner/))

(1) __Swap `left_control` and `left_command`__ (_Simple Modification_)
{% asset_img "karabiner/simple_modification.png"%}

(2) __Backslash to Forward Delete__ [<a href="karabiner://karabiner/assets/complex_modifications/import?url=https://cdn.rawgit.com/zlargon/e9e8a74bb74f56d908ca2cb8ad06427e/raw/765f396ab2ebe76d252116419d922fe3499de62f/karabiner_backslash_to_forward_delete.json">Click to Import</a>] (_Complex Modification_)

{% asset_img "karabiner/complex_modification_1.png"%} <br>
{% asset_img "karabiner/complex_modification_2.png"%}

## 10. Alfred 2 ([download](https://www.alfredapp.com/))

{% asset_img "alfred/preference.png"%}

| Title            | Keyword | Search URL |
| ---              | ---     | --- |
| Messenger        | `msg`   | `https://www.messenger.com/` |
| Yahoo Dictionary | `y`     | `https://tw.dictionary.yahoo.com/dictionary?p={query}`|
| Google Maps      | `m`     | -- |
| Translate        | `f`     | -- |
| Gmail            | `g`     | -- |
| Youtube          | `you`   | -- |
| Facebook         | `fb`    | -- |

## 11. Sublime Text 3 ([download](https://www.sublimetext.com/3))

(1) Enable [__Sublime Text Command Line__](https://www.sublimetext.com/docs/3/osx_command_line.html)

``` bash
mkdir ~/bin
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" ~/bin/subl
```

{% codeblock "~/.bash_profile" lang:bash %}
# export ~/bin
export PATH=~/bin:$PATH
{% endcodeblock %}

{% asset_img "sublime_text/bash_profile.png"%}

(2) Enable [__Sublime Package Control__](https://packagecontrol.io/installation)

Use <code>Ctrl + `</code> to open the console and paste the code in it.
{% asset_img "sublime_text/package_control.png"%}

(3) __Install Packages__
- `HTML-CSS-JS Prettify`
- `Babel`
- `MarkdownLight`
- `GitGutter`

Use `Cmd + Shift + P` to search package control.
{% asset_img "sublime_text/install_package_1.png"%}

Search the name of packages.
{% asset_img "sublime_text/install_package_2.png"%}

(4) __Preferences.sublime-setting__ (use `Cmd + ,` to open preference)

``` json
{
  "tab_size": 2,
  "translate_tabs_to_spaces": true,
  "trim_trailing_white_space_on_save": true,
  "ensure_newline_at_eof_on_save": true,
  "auto_complete_selector": "source, text",
  "folder_exclude_patterns": [".svn", ".git", ".hg", "CVS", "node_modules"]
}
```

{% asset_img "sublime_text/preference.png"%}

## 12. [Brew](https://brew.sh/)

``` bash
# install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> Note: `git` will be installed during the installation.

## 13. [Node.js](https://nodejs.org/), [NVM (Node Package Manager)](https://github.com/creationix/nvm)

``` bash
# install nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
 
# install node via nvm
nvm ls-remote --lts
nvm install --lts
 
# update npm (Node Package Manager)
npm install -g npm
 
# download yarn via brew (alternative of npm)
brew install yarn --without-node
```

## 14. [Git](https://git-scm.com/)

``` bash
# install git via brew
brew install git
```

(1) Git config and alias

``` bash
# config
git config --global color.ui       true
git config --global core.editor    vim
git config --global core.quotepath false
 
# git alias
git config --global alias.br  branch
git config --global alias.co  checkout
git config --global alias.cp  cherry-pick
git config --global alias.st  stash
git config --global alias.sub submodule
```

(2) [git-completion](https://github.com/git/git/blob/master/contrib/completion/git-completion.bash)

```
# Download git-completion.bash
curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash > ~/.git-completion.sh
```

{% codeblock "~/.bash_profile" lang:bash %}
# git bash completion
[ -f ~/.git-completion.sh ] && . ~/.git-completion.sh
{% endcodeblock %}

{% asset_img "git/completion.png"%}

(3) [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy)

``` bash
# install diff-so-fancy via yarn
yarn global add diff-so-fancy

# use diff-so-fancy to diff code
git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"
```

## 15. Audacity ([download]](http://www.audacityteam.org/download/mac/))

(1) Install LAME 3.99.5 for Audacity [download](https://lame.buanzo.org/#lameosxdl)
(2) Set shortcut `cmd + shift + E` for `Export Selected Audio ...`
{% asset_img "audacity/config.png"%}

## 16. Other Apps (13)

- [Chrome](https://www.google.com/chrome/)
- [Skitch](https://itunes.apple.com/us/app/skitch-snap-mark-up-share/id425955336?mt=12)
- [Memory Clean](https://itunes.apple.com/us/app/memory-clean-2-free-up-memory/id1114591412?mt=12)
- [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)
- [AppCleaner](http://www.freemacsoft.net/appcleaner/)
- [Acrobat Reader](https://acrobat.adobe.com/us/en/acrobat/pdf-reader.html)
- [Teamviewer](https://www.teamviewer.us/)
- [VLC](http://www.videolan.org/vlc/)
- [F.lux](https://justgetflux.com/)
- [Anki](https://apps.ankiweb.net/)
- [Keyboard Clean Tool](https://folivora.ai/keyboardcleantool/)
- [Android File Transter](https://zlargon.github.io/blog/MAC/others/stop-android-file-transfer-auto-starting/)

# Reference

- https://support.apple.com/en-us/HT204904
- https://support.apple.com/en-us/HT204156
- https://zlargon.github.io/blog/MAC/tools/mac-terminal/
- https://zlargon.github.io/blog/MAC/tools/touchpad-setting/
- https://zlargon.github.io/blog/MAC/tools/keyboard-setting/
- https://zlargon.gitbooks.io/git-tutorial/content/config.html
- https://stackoverflow.com/questions/12656448/sublime-text-2-auto-completion-popup-does-not-work-properly
