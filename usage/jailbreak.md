---
description: Learn how to jailbreak your device with palera1n
---

# Jailbreak

## Rootful (recommended) <sub>(for now)</sub>
* #### First jailbreak
  * Run `./palera1n -f -c`
* #### If you've already jailbroken before/created the fakefs
  * Run `./palera1n -f`

### If you don't have enough space for the fakefs (16GB device, or just not enough space)
* #### First jailbreak
  * Run `./palera1n -f -B`<details><summary>What does this do?</summary>This creates the fakefs but with bind mounts, so it uses a smaller size at the expense of having unwritable parts in rarely-written paths. </details>

* #### If there still isn't enough space, you will have to use palera1n tethered using the [original Shell script](https://github.com/palera1n/palera1n). The C rewrite does not support tethered use at this time.


## Rootless
* Just run `./palera1n`

Please keep in mind that that tweak support is very minimal on rootless.

<br>

### All arguments and further information about palera1n-c can be found [here](https://cdn.nickchan.lol/palera1n/artifacts/c-rewrite/palera1n.1.html).
