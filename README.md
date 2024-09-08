<<<<<<< HEAD
### **Environment Setup for Ubuntu Touch Porting on Fedora**

This section documents the steps required to set up the build environment for porting Ubuntu Touch to the Galaxy A11q on Fedora.

---

#### **1. Install Repo Tool**
First, install the `repo` tool used for managing Android source code:

```bash
sudo dnf install repo
```

#### **2. Update Your PATH**
Make sure to add the `~/bin` directory to your `PATH`:

```bash
mkdir -p ~/bin
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
source ~/.bashrc
```

#### **3. Install Development Tools**
Install the required development tools using the following commands:

```bash
sudo dnf groupinstall "Development Tools"
```

#### **4. Install 32-bit Library Support**
For building and compiling, you need 32-bit library support:

```bash
sudo dnf install gcc-c++ glibc-devel.i686 libstdc++-devel.i686
```

#### **5. Install Required Dependencies**
Next, install all the required dependencies for building the project:

```bash
sudo dnf install gcc make glibc-devel bc bison \
ca-certificates cpio curl flex git kmod openssl-devel ncurses-compat-libs python3 \
unzip wget xz jq
```

#### **6. Install XML Utilities**
To handle XML-related tasks:

```bash
sudo dnf install libxml2
```

#### **7. Clone and Compile `img2simg` Tool**
The `img2simg` tool is necessary for handling sparse images. Clone and compile it as follows:

```bash
git clone https://coral.googlesource.com/img2simg
cd img2simg/libsparse
gcc -I. -Iinclude -o img2simg img2simg.c sparse_crc32.c sparse_err.c sparse_read.c sparse.c backed_block.c output_file.c -lz
```

#### **8. Move `img2simg` to System Path**
Finally, move the compiled `img2simg` binary to `/usr/local/bin` so it can be accessed globally:

```bash
sudo mv img2simg /usr/local/bin/
```
## Kernel Source

For the clean kernel source with Halium patches, please visit our [GitLab repository](https://gitlab.com/luisvinatea/kernel-sm-a115m-latin-rr-opensource).

This repository focuses on the Ubuntu Touch porting process for the Samsung Galaxy A11q.
