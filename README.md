# TUẦN 4: Build Embedded Linux cho BeagleBon Black bằng Buildroot.
# I. Mục tiêu
- Hiểu quy trình xây dựng hệ điều hành nhúng
- Nắm được cấu trúc hệ thống Linux Embedded
- Thực hành build bootloader, kernel và root filesystem

# II. Các bước thực hiện
## Bước 1: Cài đặt các gói phụ thuộc
sudo apt update
sudo apt install build-essential libncurses-dev \
git bc bison flex texinfo unzip wget rsync \
libssl-dev python3 python3-pip python3-setuptools \
libcurl4-openssl-dev -y
