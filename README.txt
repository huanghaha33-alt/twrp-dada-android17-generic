Xiaomi 15 (dada) — Android 17 generic experimental TWRP

Target: Xiaomi 15 codename dada running Android 17 / API 37. The image is not
locked to China, EEA or Global firmware version strings. It remains strictly
device-specific and must not be used on another model.

This is an experimental port based on the pinned TWRP-Test twrp-16.0 source,
not an official TWRP release. Stock hardware files are sourced from the verified
EEA OS4.0.8.0.XOCEUXM Android 17 full OTA because a recovery still needs real
dada firmware and HAL files. Their source partitions and payload are locked by
SHA-256, and per-file hashes are recorded during extraction.

The KeyMint guard accepts Android 17 monthly security patch properties instead
of one firmware build number. It rejects empty, malformed, Android 16, and
TWRP's synthetic OS 99 / patch level 2099 values. If the installed system does
not expose safe Android 17 properties, recovery remains bootable but data
decryption is deliberately blocked. Cross-version decryption is NOT guaranteed.

Build: Actions -> Build dada Android 17 generic TWRP -> Run workflow.
The workflow uses a public ubuntu-24.04 GitHub-hosted runner, downloads official
firmware directly from Xiaomi, syncs pinned Android/TWRP sources, builds the
kernel-less v4 recovery image, and uploads the image plus inspection reports.

Output: twrp-dada-A17-generic-exp1.img

Source pins:
  Device: YuKongA/twrp_device_xiaomi_sm8750_thales
    ba8dc259c86d8287f9260e5f393f0a4cf230f4e7
  Recovery: TWRP-Test/android_bootable_recovery
    8a58fc3b586b8a908337fa87529cfbbb119ec7bb
  update_engine:
    a4c7444f722bada4e3880a5e38b42b9aa4ee37a4
  All Android project revisions: config/pinned-manifest.xml

The generated image targets the dedicated recovery partition. Compilation and
static inspection do not prove boot, touch, decryption, MTP, Wi-Fi, backups,
restores, or OTA installation on a phone. Do not format Data to work around a
decryption failure. Test without overwriting both recovery slots.

https://github.com/TWRP-Test/platform_manifest_twrp_aosp
https://github.com/TWRP-Test/android_bootable_recovery
https://github.com/YuKongA/twrp_device_xiaomi_sm8750_thales
