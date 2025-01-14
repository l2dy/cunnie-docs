## Setting Up a New Apple Mac

```bash
git status # loads command line tools
NEW_HOST=morgoth
sudo scutil --set LocalHostName $NEW_HOST
sudo scutil --set ComputerName $NEW_HOST
sudo scutil --set HostName $NEW_HOST
diskutil rename / $NEW_HOST
```
- Copy important repos over

```bash
SOURCE_HOST=tara
# if you haven't restored Downloads from backup, copy it from another machine:
# rsync -avH --progress --stats $SOURCE_HOST\:Downloads/ ~/Downloads/
rsync -avH $SOURCE_HOST\:bin/ ~/bin/
rsync -avH $SOURCE_HOST\:aa/ ~/aa/
rsync -avH $SOURCE_HOST\:docs/ ~/docs/
rsync -avH $SOURCE_HOST\:bin-old/ ~/bin-old/
rsync -avH $SOURCE_HOST\:docs-old/ ~/docs-old/
HOSTNAME=$(hostname); cd ~/aa; git add .; git ci -m"from ${HOSTNAME%%.*}"; git pull -r; git push; cd ~/bin-old; git add .; git ci -m "from ${HOSTNAME%%.*}"; git pull -r; git push; cd ~/docs-old/ ; git add .; git ci -m "from ${HOSTNAME%%.*}"; git pull -r; git push; cd ~/docs; git pull; cd ~/bin; git pull; popd; popd; popd; popd; popd
rsync -avH --progress --stats $SOURCE_HOST\:workspace/ ~/workspace/
```
- Set up git per [git.md](https://github.com/cunnie/docs/blob/master/git.md)
- System Preferences
  - Displays → Resolution: Scaled → choose desired resolution
  - Sharing
    - Screen Sharing
    - Remote Login
  - Accessibility → Pointer Control → Mouse & Trackpad → Trackpad Options...
    - Enable dragging → three finger drag
  - Keyboard
    - Key Repeat: Fast
    - Delay Until Repeat: Short
    - ✅: Use F1, F2, etc. keys as standard function keys
    - _or_ Touch Bar shows F1, F2, etc. Keys
  - Bluetooth
    - ✅: Show Bluetooth in menu bar
    - go through each of the connected bluetooth devices:
      - Options → Connect to This Mac: When Last Connected to This Mac
  - Network → uncheck Limit IP Address Tracking
- Install brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
cd ~/bin
brew bundle # allow Oracle/Virtualbox extension when asked
brew bundle # a second time to recover from the Oracle fail
```
- Move Dock clutter into trash
- Open Firefox & configure
  - log in
  - set theme
  - open gmail
- System Preferences → Apple ID → iCloud → iCloud Drive → Options... → check:
  Desktop & Documents Folders
- Set up date in Menu Bar (24-hour, show seconds & Date)
  - System Preferences → Dock & Menu Bar → Clock Menu Bar
- System Preferences → Dock & Menu Bar → check: Automatically hide and show the Dock
- System Preferences → Security & Privacy → FileVault → Turn On FileVault
  - Allow my iCloud account...
- Messages → Preferences → iMessage → ✅: Enable Messages in iCloud
  - → Start new conversations from +1 (650) 968-6262
- (if on Desktop) System Preferences → Security & Privacy → General
  - uncheck "Require password ... after sleep or screen saver"
- on iPhone: Settings → Messages → Text Message Forwarding → _new device_ ✅
- Photos → ⌘, (Preferences) → ✅: Include location information when sharing...
- Photos → ⌘, (Preferences) → iCloud → ✅: Download Originals to this Mac
- Set up iStat Menus
  - No battery
  - Disks: show throughput, too
  - CPU: historical
- Set up JetBrains Toolbox
  - login in via Toolbox
  - update all tools automatically
  - generate shell scripts, set path to /usr/local/bin
  - Goland
  - RubyMine
- Rectangle (approve accessibility)
  - Preferences: Launch Rectangle at login
- FlyCut (approve accessibility)
  - ✅: Launch Flycut on login
  - iCloud Sync: ✅: Settings
  - Display in Menu: 99 / 99 / 99
  - ✅: Remove duplicates
  - ✅: Move posted item to top of stack
  - Appearance → Menu item icon: Black scissors
- Zoom
  - 49 participants
  - HD video
- iTerm
  - Use _nord-iterm2_ color scheme for a more pleasant terminal experience:
  ```bash
  cd ~/Downloads
  curl -L https://github.com/arcticicestudio/nord-iterm2/archive/v0.2.0.zip -o nord-iterm2.zip
  unzip nord-iterm2.zip
  ```
  - iTerm2 → ⌘, (Preferences) → Profiles → General → Working Directory → Reuse previous session's directory
  - iTerm2 → ⌘, (Preferences) → Profiles → Colors → Color Presets → Import... → `xml/Nord.itermcolors`
  - iTerm2 → ⌘, (Preferences) → Profiles → Colors → Color Presets → Nord
  - iTerm2 → ⌘, (Preferences) → Profiles → Terminal → Unlimited scrollback
  - iTerm2 → ⌘, (Preferences) → Profiles → Text → User built-in Powerline glyphs (checked)
- Set up zsh per [zsh.md](https://github.com/cunnie/docs/blob/master/zsh.md)
```bash
pip3 install neovim
git clone https://github.com/luan/nvim ~/.config/nvim
```
- Install Luan's [tmuxfiles](https://github.com/luan/tmuxfiles/blob/master/install)
```bash
curl https://raw.githubusercontent.com/luan/tmuxfiles/master/install | bash
```
- System Preferences → Users & Groups → Login Items
  - Remove GPG Mail Upgrader
  - Add Flycut
- Update IPv6 address in DNS; it has changed with reinstall
- Set up git pairs:
```bash
ln -s ~/bin/env/git-authors ~/.git-authors
```
- Install rubies:
```bash
ruby-install 3.1
ruby-install 3.0
ruby-install 2.7
ruby-install 2.6
```
- Start Google Drive
- Install GPG keys:
```
mv ~/.gnupg* /tmp/
ln -s ~/Google\ Drive/My\ Drive/keys/gnupg $HOME/.gnupg
git config --global user.signingkey 93B3BB2C9F7F5BA4
git config --global commit.gpgsign true
```
- if on laptop:
  - download Wireguard from the App Store
  - click "Import tunnel(s) from file"
  - import from `~/My Drive/wg/wg0-tetra.conf`

Install [smith](https://github.com/pivotal/smith/releases)
