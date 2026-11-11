# Prebuilt kernel provenance

- Kernel source: plmzaq2112/dandelion-4.19-purity
- Branch: 4.19.325-purity
- Commit: 155480951a28d98e82252753eb1e56997f5e7ae6
- Defconfig: blossom_purity_defconfig
- Built (UTC): 2026-11-11T11:16:35Z
- Toolchain: Ubuntu clang version 21.1.8 (6ubuntu1)

## Artifacts

| File | Bytes | SHA256 |
|---|---|---|
| kernel | 9359188 | 2d39e1dccd054f00bdb69a4d27cad3f57e3acb12b39d30b6bf72e139d7002448 |
| dtb.img | 127044 | 82bb85356992b8007bf90df26902bbdb93ad4f4a9670e2ac341d5d38a509320e |
| dtbo.img | 144732 | 4e02a5c2b9b4791c5e4c35cd40df2d5c787cbbe29bb08c2eeae8e9f9dca135e9 |

## DT blobs

`dtb.img` and `dtbo.img` are extracted from the device's stock images
(boot-backup.img, dtbo-backup.img) so the device tree matches
the hardware. Only the kernel image is replaced; see
https://github.com/plmzaq2112/dandelion-4.19-purity for the source.
