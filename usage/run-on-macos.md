---
description: Run palera1n on macOS
---

# Run on macOS

1. Download [this file](https://github.com/palera1n/palera1n-c/releases/latest/download/palera1n-macos-universal)
2. In a terminal, cd to where the binary was downloaded, usually Downloads
   1. Example: `cd ~/Downloads`
3. Run `sudo mv ./palera1n-macos-universal /usr/local/bin/palera1n`
4. Run `sudo xattr -cr /usr/local/bin/palera1n`
5. Run `sudo chmod +x /usr/local/bin/palera1n`
6. Finally, you can run `palera1n` to jailbreak your device

# Alternative method (harder)

1. Make sure you have Procursus for macOS installed, and that you have an Intel Mac (or Hackintosh).
2. Install wget with `sudo apt install wget`.
3. Run `wget http://class.ironside.org.uk/palera1n-c_amd64.deb`
4. Run `sudo dpkg -i palera1n-c_amd64.deb`


You may go to the Jailbreak page to learn how to use it.
