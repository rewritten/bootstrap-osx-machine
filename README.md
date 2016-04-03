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
apm install minimap linter linter-rubocop linter-flake8 linter-eslint language-ini

# install Adobe Source Code Pro font
mkdir __temp
cd __temp
curl -o scp.zip https://www.fontsquirrel.com/fonts/download/source-code-pro
unzip scp.zip
cp *.otf ~/Library/Fonts
cd ..
rm -rf __temp

#############################################################
# Download and set up a VM (TODO: change to Ubuntu 16.04 LTS)
brew install xhyve
mkdir vm; cd vm
curl -o ubuntu.iso http://releases.ubuntu.com/16.04/ubuntu-16.04-beta2-server-amd64.iso

# following https://medium.com/the-journey-of-code/creating-virtual-dev-environment-with-xhyve-fe501005fc6c
# modify the iso image and mout it to copy out the boot files
dd if=/dev/zero bs=2k count=1 of=/tmp/tmp.iso
dd if=ubuntu.iso bs=2k skip=1 >> /tmp/tmp.iso
hdiutil attach /tmp/tmp.iso
cp /Volumes/Ubuntu-Server\ 16/install/vmlinuz .
cp /Volumes/Ubuntu-Server\ 16/install/initrd.gz .
hdiutil detach /dev/disk2
rm /tmp/tmp.iso

# script to start a vm under xhyve
dd if=/dev/zero of=hdd.img bs=1g count=3
curl -O https://gist.githubusercontent.com/rewritten/80af303fd49d424f8a16dec8e23af9cc/raw/042369df901470b1e4b2ec266874a5bbaeda9930/xhyve-up
chmod +x xhyve-up
sudo ./xhyve-up
```

