Update the system 

Config the system

[装点你的 Dock](https://sspai.com/post/33493)



Remove all Dock icons

Launchpad default order: - the first screen is Apple's application

`defaults write com.apple.dock ResetLaunchPad -bool true; killall Dock`

Install Howbrew

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

update the brew

`brew update && brew upgrade && brew cleanup`



install - xCode Chrome intelliJ iTerm2 1Password Alfred3 youdaoDict wechat typora  clipy

iTerm2- shortcut [其他快捷键](https://mail.google.com/mail/u/0/#m_2323544768683095119_%E5%85%B6%E4%BB%96%E5%BF%AB%E6%8D%B7%E9%94%AE) [Keyboard Shortcuts](http://ss64.com/bash/syntax-keyboard.html) 

spectacle - 窗口管理工具



install - [Oh My Zsh](http://ohmyz.sh/)

`sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`

`cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc`  重置 ~/.zshrc

`$HOME/bin`    自定义脚本

plugin [有价值的插件](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins-Overview)  [git-alais 默认启用](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugin:git)



config Github:

run `ssh-keygen` to create ssh key. paste `id_rsa.pub` to github settings



install subline

```
brew cask install sublime-text		
```



config sourceTree:

login with jfliu@thoughtworks.com and Oauth with GitHub



Install

