---
description: Learn how to restorerootFS with palera1n-c
---

# restorerootFS on Linux with palera1n-c

## Restart usbmuxd (**Linux ONLY**)

In a second terminal window, run the following commands:

1. `sudo systemctl stop usbmuxd`
2. `sudo usbmuxd -f -p`

## restorerootFS 

This guide assumes that you have already downloaded and setup palera1n-c. Use `sudo` if you are on Linux. 

If you jailbroke rootful (fakeFS or bindFS), run `palera1n --force-revert -f`

If you jailbroke rootless, run `palera1n --force-revert`
