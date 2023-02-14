---
description: Run palera1n on Linux
---

# Run on Linux

## Restart usbmuxd

In a second terminal window, please run the following commands:

1. `sudo systemctl stop usbmuxd`
2. `sudo usbmuxd -f -p`

## Jailbreak

1. Download one of the files below
   * [x86\_64](https://github.com/palera1n/palera1n-c/releases/download/v2.0.0-beta.3/palera1n-linux-x86\_64) (64-bit, most common)
   * [x86](https://github.com/palera1n/palera1n-c/releases/download/v2.0.0-beta.3/palera1n-linux-x86) (32-bit)
   * [arm64](https://github.com/palera1n/palera1n-c/releases/download/v2.0.0-beta.3/palera1n-linux-arm64)
   * [armel](https://github.com/palera1n/palera1n-c/releases/download/v2.0.0-beta.3/palera1n-linux-armel)
2. In a terminal, cd to where the binary was downloaded, usually Downloads
   * Example: `cd ~/Downloads`
3. Run `sudo mv ./palera1n-linux-* /usr/bin/palera1n`
4. Run `sudo chmod +x /usr/bin/palera1n`

You may go to the [Jailbreak](jailbreak.md) page to learn how to use it.
