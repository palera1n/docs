---
description: Migrate from the old palera1n.sh
---

# Migration from palera1n.sh

Before using palera1n-c or palen1x, you may need to restorerootFS first depending on how you used palera1n.sh. 

## If you used Tethered

**Please keep in mind that 16 GB devices are not supported with a full fakeFS, you will need to use the experimental bindFS feature**, so it may be better to stay on tethered palera1n.sh 

1. Go into your palera1n folder, or clone a new one if needed
2. Run `./palera1n.sh --tweaks <your iOS version> --restorerootfs`
   1. If on Linux, make sure to use `sudo` and make sure that [usbmuxd is restarted](run-on-linux.md#restart-usbmuxd)
3. Go to the usage guide for your platform

## If you used Semi-tethered (fakeFS)

You don't need to do anything, just go to the usage guide for your platform.
