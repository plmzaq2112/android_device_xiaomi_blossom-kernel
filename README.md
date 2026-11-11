# android_device_xiaomi_blossom-kernel

Prebuilt kernel artifacts for the Xiaomi blossom family (Redmi 9A / 9C / 10A /
Poco C3, MT6765), consumed by the crDroid device tree at
`device/xiaomi/blossom-kernel`.

## Layout

```
kernel      # gzip-compressed arm64 Image (Image.gz), magic 1f 8b
dtb.img     # device tree blob embedded into boot.img
dtbo.img    # device tree overlay image (separate dtbo partition)
PROVENANCE.md
```

`device/xiaomi/blossom/BoardConfig.mk` sets:

```
TARGET_PREBUILT_KERNEL   := $(DEVICE_PATH)-kernel/kernel
TARGET_PREBUILT_DTB      := $(DEVICE_PATH)-kernel/dtb.img
BOARD_PREBUILT_DTBOIMAGE := $(DEVICE_PATH)-kernel/dtbo.img
TARGET_FORCE_PREBUILT_KERNEL := true
```

so no kernel source is needed in the ROM tree.

## Source

- Kernel: https://github.com/plmzaq2112/dandelion-4.19-purity
- Branch: `4.19.325-purity`
- Defconfig: `blossom_purity_defconfig`
- Toolchain: clang 21 + LLD + `aarch64-linux-gnu-`

## Design rule

Only the kernel image is replaced. `dtb.img` / `dtbo.img` are extracted from
the device's stock images so that the hardware description stays exactly as
shipped by Xiaomi. This mirrors the kernel project's own boot repack flow
(stock ramdisk and DT preserved, kernel replaced).

## Regenerating

```bash
# in the ROM project repository
tools/make-kernel-prebuilt.sh <kernel-src> <out-dir> <stock-boot.img> <stock-dtbo.img>
```

The script writes `PROVENANCE.md` with commit, build time and SHA256 of every
artifact. Commit the artifacts and the provenance file together; never update
one without the other.
