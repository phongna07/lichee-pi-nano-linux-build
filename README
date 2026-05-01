# Buildroot cho Lichee Pi Nano

## Giới thiệu

Repo sử dụng **Buildroot** để build image cho vi điều khiển **Lichee Pi Nano**. Bài tập cho FPT Telecom Embedded Bootcamp 2026.

## Cấu trúc Build Image

### 1. Cấu hình chung (file genimage.cfg)

Tệp cấu hình chính nằm tại: `board/sipeed/licheepi_nano/genimage.cfg`

```ini
image sdcard.img {
	hdimage {
	}

	partition u-boot {
		in-partition-table = "no"
		image = "u-boot-sunxi-with-spl.bin"
		offset = 8k
		size = 512k
	}

	partition boot {
		partition-type = 0xC
		bootable = "true"
		image = "boot.vfat"
	}

	partition rootfs {
		partition-type = 0x83
		image = "rootfs.ext4"
	}
}

image boot.vfat {
	vfat {
		files = {
			"zImage",
			"suniv-f1c100s-licheepi-nano.dtb"
		}
	}
	size = 32M
}
```

### 2. Yêu cầu Build U-Boot

`u-boot-sunxi-with-spl.bin` → được ghi vào phân vùng u-boot tại offset 8k với kích thước 512k

### 3. Build Linux Kernel (zImage)

`zImage` (kernel image) → được đặt trong phân vùng boot

### 4. Tạo Root Filesystem (RootFS)

`rootfs.ext4` → được ghi vào phân vùng rootfs

### 5. Generate Image (sdcard.img)

Công cụ **genimage** sử dụng file cấu hình `genimage.cfg` để tạo image cuối cùng.

**Kết quả build**: [sdcard.img](./output/images/sdcard.img) file image hoàn chỉnh nằm trong [output/images/](./output/images/)