## Ubuntu Touch Porting for Samsung Galaxy A11q on Fedora

### Introduction

This guide provides step-by-step instructions to set up a development environment on Fedora for porting Ubuntu Touch to the Samsung Galaxy A11q. We will cover everything from setting up the necessary tools and libraries to unpacking the stock firmware and extracting critical kernel and boot image details.

### Environment Setup

#### 1. Install Repo Tool

The `repo` tool is used for managing Android source code. Install it using the following command:

```bash
sudo dnf install repo
```

#### 2. Update Your PATH

Add the `~/bin` directory to your PATH environment variable:

```bash
mkdir -p ~/bin
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
source ~/.bashrc
```

#### 3. Install Development Tools

Install a set of development tools required for building Android kernels:

```bash
sudo dnf groupinstall "Development Tools"
```

#### 4. Install 32-bit Library Support

Ensure 32-bit libraries are installed for cross-compilation purposes:

```bash
sudo dnf install gcc-c++ glibc-devel.i686 libstdc++-devel.i686
```

#### 5. Install Required Dependencies

The following packages are needed for building the kernel and managing related tasks:

```bash
sudo dnf install gcc make glibc-devel bc bison \
ca-certificates cpio curl flex git kmod openssl-devel ncurses-compat-libs python3 \
unzip wget xz jq
```

#### 6. Install XML Utilities

To handle XML files, you need `libxml2`:

```bash
sudo dnf install libxml2
```

#### 7. Clone and Compile the `img2simg` Tool

The `img2simg` tool is necessary to convert Android sparse images to standard image formats. Follow these steps:

```bash
git clone https://coral.googlesource.com/img2simg
cd img2simg/libsparse
gcc -I. -Iinclude -o img2simg img2simg.c sparse_crc32.c sparse_err.c sparse_read.c sparse.c backed_block.c output_file.c -lz
```

#### 8. Move `img2simg` to System Path

Move the compiled binary to the `/usr/local/bin` directory for global access:

```bash
sudo mv img2simg /usr/local/bin/
```
## Kernel Source

For the clean kernel source with Halium patches, please visit our [GitLab repository](https://gitlab.com/luisvinatea/a11-halium-kernel).

This repository focuses on the Ubuntu Touch porting process for the Samsung Galaxy A11q.

---

### Working with Stock Firmware

#### Extracting `boot.img` and `dtbo.img`

1. **Download Stock Firmware:**
   Download the appropriate stock firmware for your device (Samsung Galaxy A11). Tools like **Frija** or websites like **SamMobile** can help you obtain official firmware files.

2. **Extract the `.tar.md5` Firmware:**
   Once downloaded, untar the `.tar.md5` file to access the various partitions:

   ```bash
   tar -xvf firmware.tar.md5 -C ~/temp
   ```

   After extraction, you'll see `.img` files such as `boot.img.lz4`, `dtbo.img.lz4`, and `vendor_boot.img.lz4`.

3. **Decompress `.lz4` Files:**
   Use the `lz4` tool to decompress the `boot.img` and `dtbo.img` files:

   ```bash
   lz4 -d boot.img.lz4 boot.img
   lz4 -d dtbo.img.lz4 dtbo.img
   ```

4. **Unpack `boot.img`:**
   After decompression, use the `unpack_bootimg.py` script to extract kernel offsets and other essential data:

   ```bash
   python3 unpack_bootimg.py --boot_img boot.img --out out
   ```

---

### Filling in Device Information

After unpacking the `boot.img`, extract key values and fill them in your `deviceinfo` file:

- **Page Size:** `deviceinfo_flash_pagesize="2048"`
- **Kernel Load Address:** `deviceinfo_flash_offset_kernel="0x80008000"`
- **Ramdisk Load Address:** `deviceinfo_flash_offset_ramdisk="0x82000000"`
- **Second Bootloader Load Address:** `deviceinfo_flash_offset_second="0x00000000"` (if applicable)
- **Kernel Tags Load Address:** `deviceinfo_flash_offset_tags="0x81e00000"`
- **DTB Address:** `deviceinfo_flash_offset_dtb="0x81f00000"`
- **OS Version:** `deviceinfo_bootimg_os_version="12.0.0"`
- **OS Patch Level:** `deviceinfo_bootimg_os_patch_level="2023-11"`
- **Command Line Args:** 
  ```bash
  deviceinfo_kernel_cmdline="console=ttyMSM0,115200,n8 androidboot.console=ttyMSM0 androidboot.hardware=qcom user_debug=30 msm_rtb.filter=0x237 ehci-hcd.park=3 androidboot.bootdevice=7824900.sdhci lpm_levels.sleep_disabled=1 earlycon=msm_hsl_uart,0x78af000 androidboot.usbconfigfs=true vmalloc=300M loop.max_part=7"
  ```
