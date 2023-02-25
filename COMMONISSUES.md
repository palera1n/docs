---
description: Common issues that users have
---


# Common Issues


## Table of Contents

- ### palera1n-c specific
    1. [jbinit DIED! (palera1n-c)](#jbinit-died-palera1n-c)
    2. [Timed out waiting for downloaad mode](#timed-out-waiting-for-download-mode)
    3. [palen1x boots into grub rescue shell](#palen1x-boots-into-grub-rescue-shell)
    4. [Stuck on PongoOS](#stuck-on-pongoos)
    5. [USB Error before booting kernel](#usb-error-before-booting-kernel)
    6. [panic: mount exited (exit status 66)](#panic-mount-exited-exit-status-66)
- ### Shell version (deprecated) specific
    1. ["Booted device" but not booted](#booted-device-but-not-booted)
    2. [Your local changes would be overwritten by checkout](#your-local-changes-would-be-overwritten-by-checkout)
    3. [jbinit DIED! (sh)](#jbinit-died-sh)
    4. [Pressing "install" on each jb](#pressing-install-on-each-jb)
    5. [End of central-directory signature not found](#end-of-central-directory-signature-not-found)
    6. [Stuck at waiting for network](#stuck-at-waiting-for-network)
    7. [Found the USB handle followed by an error occurred](#found-the-usb-handle-followed-by-an-error-occurred)
    8. [pip error: legacy-install-failure](#pip-error-legacy-install-failure)
    9. [Permission denied (publickey, password)](#permission-denied-publickey-password)
- ### No specificity to version
    1. [NewTerm not launching](#newterm-not-launching)
    2. [palera1n/mineek repo not working](#palera1nmineek-repo-not-working)
    3. [Procursus "killed 9"](#procursus-killed-9)
    4. [App crashes on open](#app-crashes-on-open)
    5. [Please reinstall Sileo via SSH](#please-reinstall-sileo-via-ssh)
    6. [Loader app not appearing](#loader-app-not-appearing)
    7. [Could not connect to lockdownd](#could-not-connect-to-lockdownd)
    8. [Error installing bootstrap. Status: -1](#error-installing-bootstrap-status--1)
    9. [Daemons crashing on iOS 16.2+](#daemons-crashing-on-ios-162)
    10. [Panics making loader not appear](#panics-making-loader-not-appear)
    11. [libhooker wants to install?](#libhooker-wants-to-install)
    12. [Restoring rootfs still keeps app icons??](#restoring-rootfs-still-keeps-app-icons)
    13. [Device boots out of DFU](#device-boots-out-of-dfu)
    14. [SEP Panic: :skg /skgs](#sep-panic-skg-skgs)
    15. [Cannot download apps from App Store](#cannot-download-apps-from-app-store)
    16. [Snowboard theming incorrectly](#snowboard-theming-incorrectly)
    17. [Filza crashing on launch](#filza-crashing-on-launch)
    18. [dpkg error: Read-only file system](#dpkg-error-read-only-file-system)
    19. [Library not loaded: /usr/lib/libSystem.B.dylib](#library-not-loaded-usrliblibsystembdylib)
    20. [No space left on device](#no-space-left-on-device)
    21. [Third-party daemons not loading on iOS 16](#third-party-daemons-not-loading-on-ios-16)
    22. [RocketBootstrap not working (apps crashing, respring loops)](#rocketbootstrap-not-working-apps-crashing-respring-loops)
    23. [Cannot install tweaks - Depends mobilesubstrate](#cannot-install-tweaks---depends-mobilesubstrate)
    24. [Decrypting apps on palera1n](#decrypting-apps-on-palera1n)
    25. [Sileo shows red "Queued" error](#sileo-shows-red-queued-error)
    26. [AppSync Unified not working](#appsync-unified-not-working)
    27. [Installing Linux without USB](#installing-linux-without-usb)
    28. [No such file or directory errors on device](#no-such-file-or-directory-errors-on-device)
    29. [Sileo error: Didn't find architectures ["iphoneos-arm64"]](#sileo-error-didnt-find-architectures-iphoneos-arm64)

### palera1n-c specific

#### jbinit DIED! (palera1n-c)
The exact cause depends on the preceding error messages, so send a log. A common cause is trying to use the create fakefs (`-c`) option when rejailbreaking. You need to remove that option if it's not your first time jailbreaking since last restoring rootfs.

#### Timed out waiting for download mode
This is usually caused by a bad DFU state. Reboot and try again.

Things to check:
- Use a USB-A cable, not USB-C.
  - If you have an Apple Silicon Mac, you may need a USB hub rather than a single-cable adapter.
- Start from normal or recovery mode, as going straight to DFU usually causes issues.
- Use a computer with an Intel or Apple Silicon CPU, as AMD has issues.

As a last resort, you can try using the legacy palera1n.sh instead, though do note that doesn't support some features like passcode on A10 or bindfs (you can use tethered instead).

#### palen1x boots into grub rescue shell
If you are using Rufus, you need to flash palen1x in DD mode, not ISO mode.

#### Stuck on PongoOS
If you're stuck at `Booting pongoOS` or `Found Pongo USB mode device`:
1. Kill the script by pressing Ctrl+C
2. Type `exit`
3. Then retry. Don't reboot the device. 

This happens happens on A9 and older devices.

If it still doesn't work, you can also try unplugging and replugging the device.

**Make sure you created fakeFS/bindFS before jailbreaking with rootful, or else you'll also be stuck on the pongoOS screen.**

#### USB Error before booting kernel
If there is only one USB Error, you can ignore it.

#### panic: mount exited (exit status 66)
You are trying to use bindFS on iOS 16, which is not currently supported. If you have enough storage, use fakeFS, otherwise use rootless (very limited tweak support) or palera1n.sh tethered.

### Shell version (deprecated) specific

#### "Booted device" but not booted
This may happen when the downloading and patching process is interrupted. Please run `./palera1n.sh clean` (use with `sudo` if on Linux), then try again.

If that doesn't fix it, it may be caused by an update from the Procursus repo. The quickest way to fix it is `./palera1n.sh --restorerootfs`. Alternatively, you can manually restore `/usr/libexec/dirs_cleaner` from the rootfs snapshot using the SSHRD script.

#### Your local changes would be overwritten by checkout
Run the following commands, and then try again:
- `cd ramdisk`
- `git stash`
- `git stash drop`
- `cd ..`

#### jbinit DIED! (sh)
Your device may get stuck on a verbose boot screen, and if you look closely you'll see a "jbinit DIED!" error near the top.

The simplest way to fix this is to `rm -rf blobs` (use `sudo` if on Linux), then force reboot your device and try to jailbreak again.

Advanced users can also try re-copying the `other/rootfs` files manually to the device using SSHRD.

#### Pressing "install" on each jb
**DO NOT DO THIS**. It resets your package lists and will likely break your jailbreak install eventually. Instead, press the gear icon, and then press Do All.

If you managed to mess up your jailbreak this way, [restore rootfs](https://ios.cfw.guide/removing-palera1n/).

#### End of central-directory signature not found
If the error message says `palera1n.zip`, you are running an outdated version of palera1n and need to update using `git pull`. If that doesn't work, see reclone palera1n.

Otherwise, this error most likely indicates a problem with your internet connection, and you simply need to try running palera1n.sh again.

#### Stuck at waiting for network
This is usually caused by a network issue.

1. Make sure you're on the latest commit (`git pull`)
2. Make sure you can access [this site](https://static.palera.in/)

If you can access it but the script still doesn't work, your network may be unstable or certain outgoing requests may be blocked. If you cannot access it, this may mean that your network is blocking it, or it's currently down.

It may also happen if you're using an AMD CPU. AMD CPUs have an issue [with (likely) their USB controllers] that causes them to have a very low success rate with checkm8.

#### Found the USB handle followed by an error occurred
This will happen if the device is in a bad DFU state, which could randomly happen, or happen if you held the 2nd DFU button for too long (volume down on iPhone X, for example).

Reboot and rerun the script, and make sure to follow the DFU helper exactly, and let go as soon as it says it found the device in DFU.

#### pip error: legacy-install-failure
- **Ubuntu/Debian**
  - `sudo apt install python3-dev`
- **Fedora**
  - `sudo dnf install python3-devel`
- **openSUSE**
  - `sudo zypper install python3-devel`
- **macOS**
  - Install Xcode Command Line Tools using:
    - `xcode-select --install`
  - If it still doesn't work, try the following command:
    - `ARCHFLAGS="-arch $(uname -m)" python3 -m pip install --compile pyimg4`

#### Permission denied (publickey, password)

If you get this error while using palera1n.sh:
1. Run `./palera1n.sh --clean && rm -rf blobs` 
2. Try jailbreaking again.

### No specificity to version

#### NewTerm not launching

Install NewTerm 2 from the [palera1n strap repo](https://repo.palera.in/) or get NewTerm 3 beta from [Chariz](https://chariz.com/get/newterm-beta).

#### palera1n/mineek repo not working
https://repo.palera.in/ and https://mineek.github.io/repo are supposed to be used on rootless jailbreaks, not with jailbreaks with fakefs or tethered that have root access.

#### Procursus "killed 9"
Binaries will need to be resigned by the Procursus Team to fix Killed: 9. In the meantime, use the palera1n strap repo. You can install it from [nebula’s repo](https://apt.itsnebula.net).

#### App crashes on open

Refer to [this](#rocketbootstrap-not-working-apps-crashing-respring-loops) first.

Otherwise, run this in NewTerm or SSH:
- `ldid -s /Applications/<appname>.app`
  - Don't include the <>

#### Please reinstall Sileo via SSH
If you have AutoSign installed and you reinstall/update Sileo, you'll get the error message shown in the screenshot. Here's how to fix it.

1. Get access to a terminal by either using SSH or NewTerm
2. Type `sudo apt remove autosign`. Unless you changed it, the password is `alpine`.
3. Once it's done, type `sudo apt reinstall org.coolstar.sileo`.
4. Try running Sileo again. Feel free to upgrade it if that was what you were planning to do.
5. Install AutoSign again.

It should be fixed after these steps.

#### Loader app not appearing
loader app not appearing
1. Check if [this shortcut](https://www.icloud.com/shortcuts/8cd5f489c8854ee0ab9ee38f2e62f87d) works
2. Check for any panic logs. If there is any, try to post them into your support thread or the jailbreak chat.
- Send the one with latest log that starts with `panic-full` **NOT any other log**
- The log can be acquired through the iDevice that you are trying to jailbreak.
  - Go to 
    - Settings
    - Privacy
    - Analytics & Improvements
    - Analytics Data
3. [Restore rootfs](https://ios.cfw.guide/removing-palera1n) and rejailbreak.

If none of these help, make sure you're waiting enough time (15-30 seconds).

On iPads if other apps don’t appear along side the loader try installing TrollStore Helper from the [Havoc repo](https://havoc.app) and use it to install TrollStore.

#### Could not connect to lockdownd
**Mux error (-8)**
Unplug and plug your device back in.


**Pairing dialog response pending (-19)**
Accept the prompt to trust the computer on your device.

**Invalid HostID (-21)**
1. Run `idevicepair pair` (use `sudo` if on Linux)
2. Accept the prompt to trust the computer on your device if needed
3. Run `idevicepair pair` again (use `sudo` on Linux)
Alternatively, just enter recovery mode manually before jailbreaking.

#### Package is in a very bad inconsistent state
You can fix this by running this command in NewTerm or SSH:
- `sudo dpkg -r --force-remove-reinstreq <PACKAGE_NAME>`
  - Don't include the <>

#### Error installing bootstrap. Status: -1
You're not jailbroken. Sideloading the loader app on its own **will not work**.

Please run palera1n on your computer to jailbreak your phone.

#### Daemons crashing on iOS 16.2+
Older versions of Substitute may cause daemons to constantly crash on iOS 16.2 and above, which may also drain your battery. Make sure to install the latest version from the [palera1n strap repo](https://repo.palera.in/).

#### Panics making loader not appear
You may be encountering some issue related to panics and the loader “not appearing”. On A10+, make sure you have your passcode disabled before jailbreaking.

#### libhooker wants to install?
**Remove the Chimera and Odyssey repo immediately!**

These repos are not meant to be used with palera1n and are able to break your jailbreak if you install anything from them.

#### Restoring rootfs still keeps app icons??
There's an issue with restoring rootfs where it doesn’t uicache. *There is no need to worry*, this happens on a couple of other jailbreaks and serves no harm to the user or device.

Example image:
![image depicting blank icons for apps](https://media.discordapp.net/attachments/1028693596469207191/1065709922207150080/1A4B5107-DCFA-42E6-AC2D-1106CD854FC2.jpg?width=830&height=434)

#### Device boots out of DFU
Make sure to use a USB-A cable, and then follow one of the methods below to enter DFU.

- **Method 1**
  1. Make sure your device is in normal or recovery mode.
  2. Connect your device to your computer.
  3. Run
     - palera1n-c
       - `./palera1n -D`
     - palera1n-sh
       - `./palera1n.sh dfuhelper`
     - Use `sudo` if on Linux.
  4. Follow the on-screen instructions.

- **Method 2**
  1. Power off your device.
  2. Connect it to your computer or a charger
  3. As soon as the Apple logo comes on, start doing the [DFU mode sequence](https://help.ifixit.com/article/108-dfu-restore).

#### SEP Panic: :skg /skgs
This happens due to having a passcode set on A10-A11 devices when jailbreaking (or having previously set a passcode on iOS 16, even if it's currently turned off).

- iOS 15
  - Turn off your passcode.
  - Try jailbreaking again.
- iOS 16
  - Turn off your passcode.
  - Backup your device.
  - Erase from settings or restore from iTunes/Finder.
  - Restore the backup.
  - Try jailbreaking again.

On A11, you can use FakePass from https://repo.alexia.lol/ to have a passcode (and Face ID on the iPhone X, no Touch ID support on the 8 yet), but this will only work in jailbroken state. It can be bypassed by simply rebooting the device.

A10 devices boot using PongoOS, so they will natively support a passcode and Touch ID.

#### Cannot download apps from App Store
Install Choicy from [this repo](https://opa334.github.io/) and disable tweak injection into the App Store.

Alternatively, disable tweak injection globally in the Substitute app and respring. You can re-enable it after downloading the apps you wanted.

#### Snowboard theming incorrectly
You may be encountering an issue with Snowboard not theming correctly or not theming at all. To fix this, make sure you have Snowboard from [SparkDev's repo](https://sparkdev.me) to solve these issues.

Example image:
![image depicting sb issue](https://media.discordapp.net/attachments/1028693596469207191/1070014279639650345/image.png)

#### Filza crashing on launch
Install **Filza File Manager 64-bit** from the [TIGI Software repo](https://www.tigisoftware.com/repo). The version on BigBoss is outdated. You do not need AutoSign or FilzaFixer anymore.

#### dpkg error: Read-only file system
1. Open the palera1n loader app.
2. Press the gear icon.
3. Remount R/W.
4. Then try again.

#### Library not loaded: /usr/lib/libSystem.B.dylib
This usually means the fakefs wasn't created properly. It might be left over from a restore. [Restore rootfs](https://ios.cfw.guide/removing-palera1n/) and try jailbreaking again.

#### No space left on device
This means that either your iDevice or your computer does not have enough storage.

If you're live booting Linux and have a low amount of RAM, this could be the cause. Please close some programs to make more space in RAM. This would be the case if you get this error before the ramdisk boots (before the 6+ progress bars).
If you're using semi-tethered and have less than 10GB available on the iDevice, this may be the issue. Please [restore rootfs](https://ios.cfw.guide/removing-palera1n/) and clear some space on your device. Alternatively, on palera1n-c, you can create a bindfs that's about 2-3GB, however some paths that are rarely written to are read only. Usually if this is the issue, the console is spammed many times with "No space left on device" or "File or directory not found."

#### Third-party daemons not loading on iOS 16
There is a bug in launchctl that causes the loader to fail to load third-party daemons (SSH, Frida, etc.) on iOS 16.

Instructions:
1. Make sure to update launchctl from Sileo, as earlier versions had another bug that didn't allow services to load at all.
2. If the step above doesn't fix it, run this command in NewTerm:
   - `sudo launchctl load /Library/LaunchDaemons/*.plist`

#### RocketBootstrap not working (apps crashing, respring loops)
RocketBootstrap does not work as-is on iOS 15 and above, and may cause apps to crash or even respring loops, especially if installed together with Cephei. To fix this, follow the steps below.

**iOS 15.0–16.2**
1. Uninstall any existing version of RocketBootstrap you have installed
2. Remove the Odyssey repo if you have it
3. Install RocketBootstrap and RocketBootstrapFix from the [palera1n strap repo](https://repo.palera.in/).

**iOS 16.3+**
1. Remove the Odyssey repo if you have it (to make sure you don't mistakenly install full libhooker, which does not work with palera1n)
2. Add the [Havoc repo](https://havoc.app/)
3. Install libhooker-shim
   - If it wants to remove Substitute, you've done something wrong)
4. Get this deb: https://repo.theodyssey.dev/debs/rocketbootstrap_1.1.0~libhooker2-iphoneos-arm.deb
5. Open it in Sileo or Filza and install it.
6. Reboot userspace (`launchctl reboot userspace`)

**Note**: Some tweaks (e.g. Watusi) are known to not work with the Odyssey version of RocketBootstrap.

#### Cannot install tweaks - Depends mobilesubstrate
Install Substitute from the [palera1n strap repo](https://repo.palera.in/).

Alternatively, you can use ElleKit, but note that some tweaks don't yet work with it.

#### Decrypting apps on palera1n
Most app decryption tools do not currently work on palera1n; however this one is known to work but note that it requires a computer:
https://github.com/AloneMonkey/frida-ios-dump

#### Sileo shows red "Queued" error
1. Run `sudo dpkg -a --configure`.
2. Run `sudo apt install -f`.
3. Then force close and reopen Sileo.

#### AppSync Unified not working
Make sure to install the latest version from [Karen's repo](https://cydia.akemi.ai), as the one on BigBoss may be outdated.

If you're still having issues, just use TrollStore instead. You can install TrollStore Helper from [Havoc](https://havoc.app).

#### Installing Linux without USB
If you are on Windows and do not have a USB flash drive to live boot or install Linux from, you can use Wubi to dual boot Ubuntu on your computer and use palera1n from there.

Make sure to disable Secure Boot from BIOS/UEFI setup before installing Wubi. (If the option to disable it is greyed out, you may need to set an administrator/supervisor password first.)

**Please note that if something goes wrong it may be hard to recover your computer without a USB, though usually it should be recoverable from BIOS/UEFI setup.**

You can download Wubi [here](https://github.com/hakuna-m/wubiuefi/releases/download/22041r345/wubi22041r345.exe).

#### No such file or directory errors on device
If you get a bunch of "No such file or directory" errors on a verbose screen on your device or computer while jailbreaking with palera1n, it means you don't have enough storage left on your device. Refer to [here](#no-space-left-on-device).

#### Sileo error: Didn't find architectures ["iphoneos-arm64"]
You are using rootless, which doesn't support most tweaks, they will have to be updated.

If you didn't mean to use rootless, it's possible you accidentally jailbroke with palera1n-c without the `-f` option at some point, or a buggy tweak created `/var/jb` for you. In that case, try fixing it using the [rootless removal shortcut](https://www.icloud.com/shortcuts/042cdda69aa8435a8d9d6101f71a2de5). (You'll have to enable Settings → Shortcuts → Advanced → Allow Running Scripts.)



<br>

### If none of these solve your issue, please join the [Discord server](https://dsc.gg/palera1n).
