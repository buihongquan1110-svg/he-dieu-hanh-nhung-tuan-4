# TUẦN 4: Build Embedded Linux cho BeagleBon Black bằng Buildroot.
# I. Mục tiêu
- Hiểu quy trình xây dựng hệ điều hành nhúng
- Nắm được cấu trúc hệ thống Linux Embedded
- Thực hành build bootloader, kernel và root filesystem

# II. Các bước thực hiện
## Bước 1: Cài đặt các gói phụ thuộc
```bash
sudo apt update
sudo apt install build-essential libncurses-dev \
python3-dev python3-setuptools python3-pip \
libssl-dev git bc bzr cvs mercurial \
unzip wget rsync fastjar java-wrappers bison flex texinfo -y
```
## Bước 2: Tải và chuẩn bị Buildroot
- Di chuyển thư mục về home:
```bash
cd ~
```

- Clone Buildroot từ Github:
```bash
git clone https://github.com/buildroot/buildroot.git
```

- Di chuyển vào thư mục Buildroot:
```bash
cd buildroot
```

## Bước 3: Làm sạch cấu hình cũ (nếu có)
```bash
make distclean
```

## Bước 4: Cấu hình cho BeagleBon Black
- Dùng cấu hình mặc định:
```bash
make beaglebone_defconfig
```

- Mở menu cấu hình:
```bash
make menuconfig
```

## Bước 5: Cấu hình hệ thống (menuconfig)
- Chạy lệnh `make menuconfig` và thiết lập các thông số sau:
### 5.1. Target Options
- Target Architecture: ARM (little endian)
- Target Architecture Variant: cortex-A8
- Target ABI: EABIhf
- Floating point strategy: VFPv3-D16
### 5.2. Toolchain
- Toolchain type: Buildroot toolchain
- Kernel Headers: Same as kernel being built
- C library: glibc
### 5.3. Kernel
- Kernel version: Latest CIP SLTS version (5.10.162-cip24)
- Kernel configuration: Using a defconfig file
- Defconfig name: omap2plus
- Device Tree Support: Tích chọn
- Device Tree Bold names: am335x-boneblack
### 5.4. System Configuration
- Root password: (Để trống hoặc đặt tùy ý)
- Run a getty (login prompt) after boot: ttyS0 (Tốc độ 115200)

### Bước 6: Build và kết quả
- Sau khi cấu hình xong hệ thống `make menuconfig` thì ta chạy lệnh build là lệnh `make -j2`

(Nếu máy có cấu hình cao, gb nhiều thì có thể chạy `make -j4` hoặc `make -j$(nproc)`)

- Và sau khi build khoảng 3h - 4h thì ta được kết quả như ảnh dưới đây:
<img width="552" height="96" alt="image" src="https://github.com/user-attachments/assets/bb75bf91-e104-4ba0-ba39-8d67f80010b6" />

## III. Ghi vào SD card

- Để copy `sdcard.img` vào thẻ nhớ ta sử dụng lệnh
```bash
sudo dd if=output/images/sdcard.img of=/dev/sdb bs=4M status=progress
sync
```

- Kết quả thu được Image build từ Buildroot đã boot thành công trên BeagleBone Black (BBB)
<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/9f903223-9464-4f71-ac74-a633e8dd1ccd" />
<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/749ac259-85c2-4814-b081-31f1bec03da5" />





