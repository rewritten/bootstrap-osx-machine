# bootstrap-osx-machine

```
# install command line tools
xcode-select --install
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install fish git ruby
gem install rubocop

# install needed software
brew tap caskroom/cask
brew cask install iterm2 atom slack

# install Adobe Source Code Pro font
mkdir __temp
cd __temp
curl -o scp.zip https://www.fontsquirrel.com/fonts/download/source-code-pro
unzip scp.zip
cp *.otf ~/Library/Fonts
cd ..
rm -rf __temp
```

