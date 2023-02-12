---
description: Learn how to jailbreak your device with palera1n
---

# Jailbreak

Make sure to prefix the commands with `sudo` if you're on Linux. Make sure your device is connected in any mode. If you're on A11, please disable your passcode before proceeding. If you're on A11 iOS 16 and had a passcode enabled, you must erase your device in settings or with iTunes on a computer. Yes, you can use a backup. Please create a backup before proceeding, anyway. While damage is unlikely and will not happen, making a backup beforehand is safe. We are **not** responsible for any damage.

If you have used palera1n semi-tethered before, you can use `palera1n -f` to boot your original fakefs.

If you have not used palera1n before, or have restored rootfs since you were using tethered, run `palera1n -cf` to create your fakefs, and when the device boots run `palera1n -f` to boot it.

To jailbreak rootless, use `palera1n` without any args. Keep in mind that tweak support is very minimal.
