---
description: Run palera1n on macOS
---

# Run on macOS

1. Enable Full Disk Access for Terminal (this only has to be done once)
   * macOS Monterey and below: System Preferences → Security & Privacy → Privacy → Full Disk Access
   * macOS Ventura and above: System Settings → Privacy & Security → Full Disk Access

   If Terminal does not show up in the list, click the plus icon and select it from Applications → Utilities.
2. If you are on macOS Monterey 12.2.1 or below, run the following commands (this only has to be done once):
   ```
   sudo python -m ensurepip
   sudo python -m pip install setuptools xattr==0.6.4
   ```
3. Download [this file](https://github.com/palera1n/palera1n-c/releases/download/v2.0.0-beta.3/palera1n-macos-universal)
4. In a terminal, cd to where the binary was downloaded, usually Downloads
   1. Example: `cd ~/Downloads`
5. Run `sudo mv ./palera1n-macos-universal /usr/local/bin/palera1n`
6. Run `sudo xattr -c /usr/local/bin/palera1n`
7. Run `sudo chmod +x /usr/local/bin/palera1n`

Visit the [Jailbreak](jailbreak.md) page to learn how to use palera1n-c
