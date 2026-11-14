# Factory file licensing and sources

This repository has **no blanket GPL license**. Sony and third-party files retain
their original copyright and license terms. The `proprietary/` directory name is
an extraction convention, not a determination that every component is closed source.

## Exact provenance

- Device: Xperia 1 VII, XQ-FS72; firmware: **71.2.A.2.35**.
- `firmware.json` identifies the source stock recovery by SHA-256.
- `proprietary-files.json` maps seven stored runtime files to original system paths.
- `recovery/files.json` maps extracted recovery files, inline data and symlinks
  to their original ramdisk paths and hashes.
- [SOURCES.json](SOURCES.json) lists every stored factory payload, its source path,
  SHA-256 and the license conclusion supported by the current evidence.

Sony publishes an [open-source archive for this exact firmware/model](https://opendevices.sony.net/file/download/open-source-archive-for-71-2-a-2-35).
That archive is a source reference, not the source of the extracted binary files
in this repository. No claim is made here that every stored binary has been
matched to corresponding source or that the archive grants rights to proprietary parts.

## Identified notices

| File | License evidence |
| --- | --- |
| `recovery/root/init.recovery.qcom.rc` | Embedded Linux Foundation redistribution notice, copied verbatim to `LICENSES/TLF-recovery-init.txt` (comment markers removed) |
| `recovery/root/system/etc/recovery.fstab` | Embedded Linux Foundation redistribution/patent disclaimer, copied to `LICENSES/TLF-recovery-fstab.txt` (comment markers removed) |
| `recovery/root/system/etc/init/android.hardware.boot-service.qti.recovery.rc` | Embedded `BSD-3-Clause-Clear` SPDX declaration and Qualcomm Innovation Center copyright |

The two Linux Foundation notices are recorded separately rather than normalized
to a different BSD license text. All embedded notices and binary bytes are retained.

## Upstream source references

These identify relevant component projects, not conclusive licenses for Sony's
exact compiled binaries or their linked dependencies:

| Stored component family | Upstream reference |
| --- | --- |
| `keystore2` | [AOSP system/security](https://android.googlesource.com/platform/system/security/) |
| `service`, `servicemanager`, Binder libraries | [AOSP frameworks/native](https://android.googlesource.com/platform/frameworks/native/) |
| ICU libraries | [AOSP external/icu](https://android.googlesource.com/platform/external/icu/) and [Unicode ICU notices](https://github.com/unicode-org/icu/blob/main/LICENSE) |
| `libdl_android`, libc and linker | [AOSP bionic](https://android.googlesource.com/platform/bionic/) |
| Recovery and fastbootd components | [AOSP bootable/recovery](https://android.googlesource.com/platform/bootable/recovery/) |
| `e2fsdroid`, `mke2fs`, ext2 libraries | [AOSP external/e2fsprogs](https://android.googlesource.com/platform/external/e2fsprogs/) |
| F2FS tools | [AOSP external/f2fs-tools](https://android.googlesource.com/platform/external/f2fs-tools/) |
| Sony/Qualcomm-specific services, policy and other blobs | Sony firmware and the source archive above; individual terms remain to be established |

`NOASSERTION` means the exact license has not been established from the available
factory notices. It does not mean proprietary, public domain, GPL, or permission
to redistribute. Metadata does not substitute for required upstream notices or
corresponding source. This inventory records the remaining gaps explicitly.
