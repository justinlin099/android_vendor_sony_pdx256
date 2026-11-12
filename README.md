# Factory dependencies

Independent vendor dependency repo, branch `twrp-3.7.1_14`, for `pdx256` / XQ-FS72.
This branch matches the companion recovery port's TWRP main version;
factory dependencies remain pinned separately to firmware 71.2.A.2.35.
Clone into `vendor/sony/pdx256` inside the companion build-integration repo.
This tree contains extraction metadata, not a complete Android vendor image
or a vendor partition build tree. Factory binaries are not modified here.

`firmware.json` pins the supported recovery digest.
`proprietary-files.json` lists seven required factory system files and SHA-256s.
The word proprietary describes the extraction tree, not a claim that every file
is closed source. The exact factory build is used for Sony runtime compatibility.

Supply a raw stock recovery image and an extracted system root with `system/bin` and `system/lib64`. SIN files are not
raw recovery images. An EROFS/ext4 system image must first be extracted using tools
appropriate to its filesystem; do not point the extractor at a mounted live Data
partition. Run `tools/extract.py --help` for input arguments.

Extraction is offline and hash checked. It never contacts the phone. Imported
files are ignored by Git, and no Sony firmware is downloaded or redistributed
by the build scripts. The device must retain matching vendor/firmware partitions;
this recovery is not a standalone replacement for those partitions.
