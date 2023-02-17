---
description: Learn how to jailbreak your device with palera1n-c
---

# Jailbreak

Make sure to prefix the commands with `sudo` if you are on Linux. 

The device can be in any mode and should be connected with a USB-A to Lightning cable before proceeding. 

If you are on A11 iOS 15, please disable your passcode before proceeding. If you're on A11 iOS 16 and have ever enabled a passcode, **you must erase your device in settings or with iTunes on a computer.** After resetting the device it is okay to use a backup. Even if you do not need to restore the device, you should still **create a backup before proceeding** in the highly unlikely case that your device is damaged. We are **not** responsible for any damage or data loss. **Use at your own risk.**

If you **have** used palera1n semi-tethered before, you can just use `palera1n -f` to boot your original fakeFS. This command may be used to rejailbreak as well. 

If you have not used palera1n before, or have restored rootFS, run `palera1n -cf` to create a fakeFS and boot it. To rejailbreak the device, use `palera1n -f`

If you are on a 16GB device, run `palera1n -Bf` to create the bindFS and boot it. To rejailbreak, run `palera1n -f`
Note that the use of a bindFS is **HIGHLY EXPERIMENTAL** and may not work as expected. It also has issues with iOS 16. **USE AT YOUR OWN RISK!!!**

To jailbreak rootless, use `palera1n` without any arguments. Keep in mind that tweak support is very minimal.

For a full list of options, run `palera1n --help`
