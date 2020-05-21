## Setting aup a New Apple Mac

```
git status # loads command line tools
scutil --set LocalHostName tetra
scutil --set ComputerName tetra
scutil --set HostName tetra
```
- Copy important repos over
```
rsync -avH --progress --stats lucy:Downloads/ Downloads/
rsync -avH lucy:bin/ bin/
rsync -avH lucy:aa/ aa/
rsync -avH lucy:docs/ docs/
rsync -avH lucy:bin-old/ bin-old/
rsync -avH lucy:docs-old/ docs-old/
HOSTNAME=$(hostname); pushd ~/aa; git add .; git ci -m"from ${HOSTNAME%%.*}"; git pull -r; git push; cd ~/bin-old; git add .; git ci -m "from ${HOSTNAME%%.*}"; git pull -r; git push; cd ~/docs-old/ ; git add .; git ci -m "from ${HOSTNAME%%.*}"; git pull -r; git push; cd ~/docs; git pull; cd ~/bin; git pull; popd
```
- Set up git per [git.md](https://github.com/cunnie/docs/blob/master/git.md)
- System Preferences
  - Sharing
    - Screen Sharing
    - Remote Login
  - Trackpad
    - Point & Click
      - Tap to click
  - Accessibility → Pointer Control → Mouse & Trackpad → Trackpad Options... 
    - Enable dragging → three finger drag
- Install brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
cd ~/bin
brew bundle # allow Oracle/Virtualbox extension when asked
brew bundle # a second time to recover from the Oracle fail
```
- Move Dock clutter into trash
- Open Firefox & configure
  - log in
  - set them
  - open gmail
- Set up date in Taskbar (show seconds & Date)
- Set up iStat Menus
- Set up JetBrains Toolbox
  - login in via Toolbox
  - Android Studio
  - Goland
  - PyCharm Community
  - RubyMine
  - WebStorm
- Spectacle (approve accessibility)
  - Preferences: Launch Spectacle at login
- FlyCut (approve accessibility)
  - Black scissors
  - Launch Flycut on login
  - Display in Menu: 40
- Set up zsh per [zsh.md](https://github.com/cunnie/docs/blob/master/zsh.md)
- Install Luan's [vimfiles](https://github.com/luan/vimfiles)
```
curl vimfiles.luan.sh/install | bash
```
- Install Luan's [tmuxfiles](https://github.com/luan/tmuxfiles/blob/master/install)
```
curl https://raw.githubusercontent.com/luan/tmuxfiles/master/install | bash
```