---
description: Flash palen1x on your USB drive
---

# Flashing palen1x

palen1x is a stripped-down Linux distribution that runs palera1n. It is based on Alpine Linux and contains everything you need to jailbreak and a simplified TUI.

You'll need a USB drive with at least 8 GB of storage. We will also assume you're on Windows, as you can run palera1n natively on macOS and Linux.

1. Plug your USB drive into your computer
2. Download the Ventoy Windows zip from [here](https://github.com/ventoy/Ventoy/releases)
3. Extract the `.zip`, and open `Ventoy2Disk.exe`
4. Select your USB drive, and click Install
   * **Please be careful to only choose the USB drive**
   * **All data on the USB drive will be erased**, please backup whatever is needed
5. Once it's done installing, download the latest palen1x from [here](https://cdn.nickchan.lol/palera1n/artifacts/palen1x)
   * The `amd64` iso is for 64-bit CPUs (AMD and Intel) and the `i686` one is for 32-bit CPUs.
     * If you're unsure on which one to choose
       1. Press the Windows key + R
       2. Type in `msinfo32` and hit enter
       3. Look for `System Type`
          * `x64-based PC` means you have a 64-bit CPU
          * `x86-based PC` means you have a 32-bit CPU
6. Drop the iso onto the new Ventoy drive in File Explorer

Done installing Ventoy and palen1x, now go to [Booting palen1x](booting-palen1x.md).
