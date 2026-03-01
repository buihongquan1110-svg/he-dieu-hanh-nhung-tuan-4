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
