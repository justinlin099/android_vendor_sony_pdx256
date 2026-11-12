# Factory dependencies

Independent vendor dependency repo, branch `twrp-14.1`, for `pdx256` / XQ-FS72.
This branch follows the companion recovery port and upstream manifest branch;
factory dependencies remain pinned separately to firmware 71.2.A.2.35.
Clone into `vendor/sony/pdx256` inside the companion build-integration repo.
This tree contains extraction metadata, not a complete Android vendor image
or a vendor partition build tree. Factory binaries are not modified here.

`firmware.json` pins the supported recovery digest.
`proprietary-files.json` lists seven required factory system files and SHA-256s.
The word proprietary describes the extraction tree, not a claim that every file
is closed source. The exact factory build is used for Sony runtime compatibility.

The private tree includes seven system runtime files under `proprietary/` and
individually extracted recovery dependencies under `recovery/root/`.
`recovery/files.json` records their hashes; empty entries and symlink payloads
are represented inline, while the device recipe retains CPIO metadata.
The original SELinux policy is included as `recovery/root/sepolicy`.
No whole or compressed stock recovery image is tracked or required to build.
No phone connection or separate factory download is required after cloning.
Image header and AVB settings are explicit in the companion device/integration
code, and unmodified upstream mkbootimg/avbtool generate the image.

`tools/extract.py` remains available in the integration repo for maintainers
importing matching raw factory files. SIN files are not raw recovery images.
The device must retain matching vendor/firmware partitions; this recovery is
not a standalone replacement for those partitions.

Build integration: https://github.com/justinlin099/twrp_sony_pdx256
Device tree: https://github.com/justinlin099/android_device_sony_pdx256
All three repositories are currently private. See NOTICE.md for factory binary
and third-party asset attribution; no blanket relicensing is implied.
