# Hardware Information Summary

## Device Provisioning
- **Device Provisioned**: The device is provisioned, indicated by `[DEVICE_PROVISIONED]: [1]`.

## Build Version and Extensions
- **Build Version Extensions (R)**: The device is running with build version extension R as `[5]`.
- **Build Version Extensions (S)**: Build version extension S is also set to `[5]`.

## Bluetooth Configuration
- **Adapter Connection State**: Cached adapter connection state is `[6242210276282834798]`.
- **Bond State**: Cached bond state for Bluetooth is `[6242210276282834794]`.
- **Profile Connection State**: Cached profile connection state is `[6242210276282834799]`.
- **Bluetooth State**: Cached Bluetooth state is `[6242210276282834800]`.
- **Offloaded Filtering Supported**: Cached value indicates offloaded filtering is supported `[6242210276282834795]`.

## Disk Usage Information

| Filesystem               | Size  | Used | Available | Use% | Mounted on  |
|--------------------------|-------|------|-----------|------|-------------|
| `/dev/block/dm-4`         | 2.4G  | 2.4G | 18M       | 100% | /           |
| `tmpfs`                   | 1.3G  | 2.0M | 1.3G      | 1%   | /dev        |
| `tmpfs`                   | 1.3G  | 0    | 1.3G      | 0%   | /mnt        |
| `/dev/block/dm-5`         | 817M  | 816M | 988K      | 100% | /product    |
| `/dev/block/dm-6`         | 559M  | 542M | 17M       | 97%  | /vendor     |
| `/dev/block/dm-7`         | 3.9M  | 1.4M | 2.5M      | 36%  | /odm        |
| `/dev/block/dm-8`         | 678M  | 185M | 493M      | 28%  | /prism      |
| `/dev/block/dm-9`         | 87M   | 920K | 86M       | 2%   | /optics     |
| `tmpfs`                   | 1.3G  | 24K  | 1.3G      | 1%   | /apex       |

### Key Observations:
- The root filesystem (`/dev/block/dm-4`) is nearly full, with 100% usage.
- The `/product` partition is also at 100% capacity.
- Several other partitions, including `/vendor` and `/odm`, are approaching full capacity.
- There is ample space available in temporary filesystems (`tmpfs`), such as for `/dev`, `/mnt`, and `/apex`.

## Display Information
### General Display Settings
- **Display Manager (Status)**:  
    - Safe Mode: `false`  
    - Pending Traversal: `false`

### Viewport Information
- **Active Viewport**:  
    - Type: `INTERNAL`  
    - Display ID: `0`  
    - Orientation: `1` (portrait mode)  
    - Logical Frame: `Rect(0, 0 - 1560, 720)`  
    - Physical Frame: `Rect(0, 0 - 1560, 720)`  
    - Device Width: `1560 px`  
    - Device Height: `720 px`

### Color and Brightness Settings
- **Default Display Color Mode**: `0` (default mode)
- **WiFi Display Scan Request Count**: `0`
- **Stable Display Size**: `720 x 1560`
- **Minimum Brightness Curve**:  
    - At 0% brightness: `(0.0, 0.0)`  
    - At 10% brightness: `(10.0, 5.0)`

## Battery Information
### Power Sources
- **AC Powered**: `false`
- **USB Powered**: `true`
- **Wireless Powered**: `false`

### Charging and Voltage
- **Max Charging Current**: `500,000 µA`
- **Max Charging Voltage**: `5,000,000 µV`
- **Charge Counter**: `4,007,520 µAh`

### Battery Status
- **Status**: `5` (Charging)
- **Health**: `2` (Good)
- **Battery Present**: `true`
- **Battery Level**: `100%`
- **Battery Scale**: `100`

### Voltage and Temperature
- **Voltage**: `4375 mV`
- **Temperature**: `22.7°C`
- **Technology**: `Li-ion`

### Miscellaneous
- **LED Charging Indicator**: `true`
- **LED Low Battery Indicator**: `true`
- **Current Now**: `0 µA`

## Memory Information
### Total and Free Memory
- **Total Memory**: `2,882,968 kB`
- **Free Memory**: `122,252 kB`
- **Available Memory**: `1,544,432 kB`

### Memory Buffers and Cache
- **Buffers**: `3,012 kB`
- **Cached Memory**: `1,479,708 kB`
- **Swap Cached**: `13,120 kB`

### Active and Inactive Memory
- **Active Memory**: `1,288,600 kB`
  - **Active (Anonymous)**: `205,664 kB`
  - **Active (File)**: `1,082,936 kB`
- **Inactive Memory**: `705,428 kB`
  - **Inactive (Anonymous)**: `321,544 kB`
  - **Inactive (File)**: `383,884 kB`

### Swap Memory
- **Total Swap Memory**: `4,194,300 kB`
- **Free Swap Memory**: `3,734,692 kB`

### Other Details
- **Dirty Memory**: `116 kB`
- **Writeback Memory**: `0 kB`
- **Mlocked Memory**: `8,504 kB`
- **Unevictable Memory**: `8,504 kB`

## CPU Information
### Processor Details
- **Processor Model**: AArch64 Processor rev 4 (aarch64)
- **Architecture**: ARMv8 Processor rev 4 (v8l)
- **BogoMIPS**: 38.40 (per core)

### CPU Features
- **Features**: 
    - `half`
    - `thumb`
    - `fastmult`
    - `vfp`
    - `edsp`
    - `neon`
    - `vfpv3`
    - `tls`
    - `vfpv4`
    - `idiva`
    - `idivt`
    - `lpae`
    - `evtstrm`
    - `aes`
    - `pmull`
    - `sha1`
    - `sha2`
    - `crc32`

### CPU Cores
- **Core 0**:
    - CPU Part: `0xd03`
    - CPU Revision: `4`
    - CPU Variant: `0x0`
    - CPU Implementer: `0x41`
- **Core 1**:
    - CPU Part: `0xd03`
    - CPU Revision: `4`
    - CPU Variant: `0x0`
    - CPU Implementer: `0x41`

### Additional Cores
- The log repeats similar information for additional cores, indicating a multi-core processor.
