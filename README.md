# 🥜 Walnut Pi — My Experience Testing Chinese Raspberry Pi Alternatives

---

## 📖 Introduction

While browsing **AliExpress** in search of affordable Chinese alternatives to the Raspberry Pi, I stumbled upon the **Walnut Pi** family. They caught my attention immediately: they were **cheaper** than a Raspberry Pi and, on paper, offered some **very interesting specs**.

So I decided to buy **two models** to test them hands-on:

- 🟢 **Walnut Pi 1B** — the budget-friendly entry-level option
- 🔵 **Walnut Pi 2B** — the more powerful, feature-packed version

---

<p align="center">
  <img src="images/t11.jpg" alt="Walnut Pi unboxing — package arrival" width="45%">
  <img src="images/t22.jpg" alt="Walnut Pi unboxing — boards inside" width="45%">
</p>

---

## 🟢 Walnut Pi 1B — Specifications

| Component | Specifications |
|---|---|
| **CPU** | Allwinner H618 — 64-bit / Quad-core Cortex-A53 @ 1.5GHz |
| **GPU** | Mali G31 MP2 — OpenGL ES 1.0/2.0/3.2 · OpenCL 2.0 |
| **RAM** | 1GB / 2GB / 4GB LPDDR4 (optional) |
| **Storage** | MicroSD up to 512GB · Reserved SPI Flash (unpopulated) |
| **WiFi** | Dual-band (2.4G & 5G) + Bluetooth 5.0 |
| **Wired Network** | 100Mbps Ethernet port |
| **Audio** | 3.5mm audio jack |
| **Video** | MicroHDMI 2.0a — supports 4K @ 60fps |
| **Peripherals** | USB 2.0 ×3 · IR ×1 · Button ×1 · LED ×1 · 40-pin GPIO (RPi-compatible) · 3-pin UART debug header |
| **Power** | USB Type-C, 5V/1A |
| **Operating Systems** | Walnut Pi OS (Debian) · Ubuntu 22.04 · Home Assistant · Android |

---

## 🔵 Walnut Pi 2B — Specifications

| Component | Specifications |
|---|---|
| **CPU** | Allwinner T527 — Octa-core Cortex-A55 64-bit @ 1.8GHz + RISC-V co-processor @ 200MHz |
| **GPU** | Mali G57 MC1 — OpenGL ES 1.1/2.0/3.2 · OpenCL 2.2 · Vulkan 1.1/1.2/1.3 |
| **NPU** | 2 TOPS — Supports INT 8/16/32-bit, Float 16/32-bit |
| **DSP** | HIFI4 @ 600MHz |
| **RAM** | 1GB / 2GB / 4GB LPDDR4 (optional) |
| **Storage** | MicroSD up to 512GB · eMMC 5.1 32GB (optional) · SPI Flash 8MB |
| **WiFi** | WiFi 6 dual-band (2.4G & 5G) + Bluetooth 5.0 · Onboard high-gain ceramic antenna · iPEX4 external antenna (optional) |
| **Ethernet** | Gigabit Ethernet (10/100/1000 Mbps auto-negotiation) |
| **Audio** | HDMI Audio · HPOUT (FPC connector) |
| **Video** | MicroHDMI 2.0a (4K @ 60fps) · MIPI Display (1×4 lane DSI, 2-lane compatible) — 1080P @ 60fps |
| **Camera** | MIPI Camera (1×4 lane CSI, 2-lane compatible) |
| **Peripherals** | PCIe 2.1 ×1 (NVMe SSD support) · USB 3.0 ×1 · USB 2.0 ×3 · IR ×1 · Programmable button ×1 · Programmable LED ×1 · 40-pin GPIO (RPi-compatible) · 3-pin UART debug header |
| **Power** | USB Type-C 5V @ 2A · PoE (Power over Ethernet) |
| **Operating Systems** | Walnut Pi OS (Debian) · Ubuntu · Android · Home Assistant |

---

## ⬇️ Downloading the OS Images

Alright, time to get to work. From the official wiki — [https://wiki.walnutpi.com/en/docs/walnutpi_1/intro/download](https://wiki.walnutpi.com/en/docs/walnutpi_1/intro/download) — you can download the OS images that need to be flashed onto a MicroSD card.

There's a dedicated section for **users outside of China**, but I was curious and wanted to try the procedure for downloading directly from **Baidu** (the "Chinese Google").

To my surprise, **my Mexican phone number was accepted** for registration — no region blocks, no workarounds needed. 🎉

After that, I installed the **Baidu Netdisk client** on my **Arch Linux** machine, and from there I downloaded the images. The transfer took **longer than expected**, but it completed without any issues.

<p align="center">
  <img src="images/t33.jpg" alt="Baidu Netdisk Download" width="65%">
</p>

---

## 💾 Flashing the Image

Once the images are downloaded, all that's left is to flash them. On Linux, I did it with `dd`:

```bash
dd if=2026-2-2_V1.7.0_WalnutPi-2B_5.15.147_debian12_server.img of=/dev/sdb bs=4M status=progress
```

And that's it — the next step is booting up. 🚀

---

## 🚀 First Boot

<p align="center">
  <img src="images/t44.jpg" alt="Boot" width="55%">
</p>

The Walnut Pi booted up without issues. I configured the WiFi network as instructed in the wiki:

```bash
nmcli dev wifi
sudo nmcli dev wifi connect XXXXX password XXXXX
```

And just like that, it connected without any problems. After that, I could connect via **SSH** to take a look at the system.

### 🖥️ System Info

```
Linux WalnutPi 5.15.147 #15 SMP PREEMPT Mon Jul 20 17:26:29 CST 2026 aarch64 GNU/Linux
```

### 🔄 System Update Check

```bash
root@WalnutPi:~# wpi-update

    Your system version is already up to [1.8.0], No need to update
root@WalnutPi:~#
```

### 📦 APT Sources

```bash
root@WalnutPi:~# cat /etc/apt/sources.list
deb http://mirrors.tuna.tsinghua.edu.cn/debian bookworm main
```

### 🧠 Memory Info

```bash
root@WalnutPi:~# free -h
               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       152Mi       1.6Gi       1.7Mi       225Mi       1.8Gi
Swap:             0B          0B          0B
```

### ⚙️ CPU Info

```bash
root@WalnutPi:~# cat /proc/cpuinfo
processor	: 0
BogoMIPS	: 48.00
Features	: fp asimd aes pmull sha1 sha2 crc32 atomics fphp asimdhp cpuid asimdrdm lrcpc dcpop asimddp
CPU implementer	: 0x41
CPU architecture: 8
CPU variant	: 0x2
CPU part	: 0xd05
CPU revision	: 0

processor	: 1
... (same for processors 1 through 7)
```

> **Note:** The system reports **8 CPU cores** (Cortex-A55, part `0xd05`), confirming the octa-core Allwinner T527.

### 🔊 Audio Devices

```bash
root@WalnutPi:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: audiocodec [audiocodec], device 0: sunxi-snd-plat-aaudio-sunxi-snd-codec 7110000.codec-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ahubhdmi [ahubhdmi], device 0: sunxi-snd-plat-i2s-sunxi-snd-codec-hdmi soc@3000000:hdmi_codec- []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Two playback devices are available: the onboard **analog audio codec** (`card 0`) and **HDMI audio** (`card 1`).

### 📡 IR Receiver

```bash
root@WalnutPi:~# ir-keytable
Found /sys/class/rc/rc0/ with:
	Name: sunxi_ir_recv
	Driver: sunxi-rc-recv
	Default keymap: rc_map_sunxi
	Input device: /dev/input/event1
	LIRC device: /dev/lirc0
	Attached BPF protocols: Operation not supported
	Supported kernel protocols: lirc nec 
	Enabled kernel protocols: lirc nec 
	bus: 25, vendor/product: 0001:0001, version: 0x0100
	Repeat delay = 500 ms, repeat period = 125 ms
```

The onboard **IR receiver** is detected and ready to use, with support for **NEC** and **LIRC** protocols.

### 🔵 Bluetooth

```bash
root@WalnutPi:~# hciconfig -a
hci0:	Type: BR/EDR  Bus: UART
	BD Address: 27:36:D2:73:7B:E0  ACL MTU: 1021:9  SCO MTU: 255:4
	UP RUNNING 
	RX bytes:811 acl:0 sco:0 events:56 errors:0
	TX bytes:2758 acl:0 sco:0 commands:56 errors:0
	Features: 0xbf 0x2e 0x4d 0xfe 0xd8 0x3f 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV3 
	Link policy: RSWITCH SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'WalnutPi'
	Class: 0x000000
	Service Classes: Unspecified
	Device Class: Miscellaneous, 
	HCI Version:  (0xd)  Revision: 0xb
	LMP Version:  (0xd)  Subversion: 0xb
	Manufacturer: not assigned (2875)
```

Bluetooth is **up and running** (`UP RUNNING`), with the adapter named `WalnutPi`. Supports BR/EDR over UART.

### 🔌 GPIO Pinout

```bash
root@WalnutPi:~# gpio pins
+---+-----------+------+----------+------+-----------+---+
| V |    Mode   | Name | Physical | Name |    Mode   | V |
+---+-----------+------+----------+------+-----------+---+
|   |           | 3.3v |  1 || 2  |   5v |           |   |
|   |  I2C1_SDA |  PB5 |  3 || 4  |   5v |           |   |
|   |  I2C1_SCL |  PB4 |  5 || 6  |  GND |           |   |
|   |       OFF |  PB6 |  7 || 8  |  PB0 | UART2_TX  |   |
|   |           |  GND |  9 || 10 |  PB1 | UART2_RX  |   |
|   |       OFF | PB13 | 11 || 12 | PB14 | OFF       |   |
|   |       OFF | PI12 | 13 || 14 |  GND |           |   |
|   |       OFF | PI11 | 15 || 16 | PI10 | OFF       |   |
|   |           | 3.3v | 17 || 18 |  PI9 | OFF       |   |
|   | SPI1_MOSI |  PI4 | 19 || 20 |  GND |           |   |
|   | SPI1_MISO |  PI5 | 21 || 22 |  PI7 | OFF       |   |
|   |  SPI1_CLK |  PI3 | 23 || 24 |  PI2 | SPI1_CS0  |   |
|   |           |  GND | 25 || 26 |  PI6 | SPI1_CS1  | 1 |
|   |  I2C2_SDA | PI16 | 27 || 28 | PI15 | I2C2_SCL  |   |
|   |       OFF |  PL6 | 29 || 30 |  GND |           |   |
|   |       OFF |  PL5 | 31 || 32 | PI14 | OFF       |   |
|   |       OFF |  PL4 | 33 || 34 |  GND |           |   |
|   |       OFF |  PL2 | 35 || 36 | PI13 | OFF       |   |
|   |       OFF |  PL3 | 37 || 38 |  PI0 | OFF       |   |
|   |           |  GND | 39 || 40 |  PI1 | OFF       |   |
+---+-----------+------+----------+------+-----------+---+

+---+-----------+------+----------+------+-----------+---+
| V |    Mode   | Name | Physical | Name |    Mode   | V |
+---+-----------+------+----------+------+-----------+---+
| 1 |        IN |  KEY | 41 || 42 |  LED | OUT       | 1 |
+---+-----------+------+----------+------+-----------+---+
```

The GPIO header is fully **Raspberry Pi-compatible**, with I2C, SPI, UART, and power pins mapped the same way. There's also an extra header (pins 41–42) for the onboard **KEY button** and **LED**, both programmable.

---

## 🗺️ Device Map

This is a really nice feature on the Walnut Pi boards. It places a **walnut icon on your country** on a world map, and also tracks the **uptime** of your device. I was really excited to see my board appear in **Mexico**… however, it seems the backend is **geoblocked**, and all devices from Mexico get grouped into the **USA** zone. 😞

But let's rewind a bit and try to understand how this neat feature actually works. 🙂

### 🔧 The Telemetry Service

The service that sends telemetry data to paint the map is called `map_device`. Let's check its status:

```bash
root@WalnutPi:~# systemctl status map_device
● map_device.service - map device
     Loaded: loaded (/lib/systemd/system/map_device.service; enabled; preset: e>
     Active: activating (start) since Wed 2026-09-09 17:28:59 CST; 23min ago
   Main PID: 1157 (map_device)
      Tasks: 4 (limit: 2226)
     Memory: 29.1M
        CPU: 788ms
     CGroup: /system.slice/map_device.service
             ├─1157 /usr/lib/walnutpi/service/map_device
             └─1180 /usr/lib/walnutpi/service/map_device

Sep 09 17:28:59 WalnutPi systemd[1]: Starting map_device.service - map device...
```

### 📡 What Gets Sent to China

When run manually, the service sends this data:

```bash
root@WalnutPi:~# /usr/lib/walnutpi/service/map_device
核桃派1代
Sent: {"chip_platform": "H618", "chip_id": "33802000ac00480801081365308f24d2", "os_version": "2.6.0", "os_type": "server"}
```

With this, the backend generates the metrics — and I assume it also grabs the **public IP** and geolocates it on the server side. 

### 🔍 Deeper Analysis of the Flow

Taking a closer look at how the metric works, the flow goes roughly like this:

```
map_device
    │
    └── Embedded Python
          │
          └── wpi_client.py
                 │
                 ├── chip_info_get()
                 │      │
                 │      ├── /sys/class/sunxi_info/sys_info
                 │      ├── /etc/WalnutPi-release
                 │      └── returns:
                 │           H618
                 │           <chipid>
                 │           2.6.0
                 │           server
                 │
                 ├── json.dumps(chip_info)
                 │
                 └── thread → send_message()
                              │
                              ├── TCP
                              │
                              ├── map.walnutpi.com:10240
                              │
                              ├── sendall(JSON)
                              │
                              └── sleep(300)
```


Although the client is a Python binary that was converted into an executable (so the code can't be read directly), I was able to **recreate its functionality almost entirely**. Here's what it does:

```python
"""
Walnut Pi Device Map terminal client code
Description: Periodically sends its own chip model and chipid to the server.
"""

import socket
import threading
import time
import os
import re
import json


def chip_info_get():
    chip_platform = None
    chip_id = None
    os_version = None
    os_type = None

    chip_platform = os.popen(
        'cat /sys/class/sunxi_info/sys_info | grep "platform"'
    ).readline()

    if 'h616' in chip_platform:
        print('Walnut Pi Gen 1')
        chip_platform = 'H618'

        id_get = os.popen(
            'cat /sys/class/sunxi_info/sys_info | grep "chipid"'
        ).readline()

        match = re.search(
            r'sunxi_chipid\s*:\s*([a-f0-9]+)',
            id_get
        )

        if match:
            chip_id = match.group(1)
        else:
            print('No chip_id found')

        os_version_get = os.popen(
            'cat /etc/WalnutPi-release | grep "version="'
        ).readline()

        match = re.search(
            r'version=(.*)',
            os_version_get
        )

        if match:
            os_version = match.group(1)
        else:
            print('No os version found')

        os_type_get = os.popen(
            'cat /etc/WalnutPi-release | grep "os_type="'
        ).readline()

        match = re.search(
            r'os_type=(.*)',
            os_type_get
        )

        if match:
            os_type = match.group(1)
        else:
            print('No os type found')

    elif 'T527' in chip_platform:
        print('Walnut Pi Gen 2')
        chip_platform = 'T527'

        id_get = os.popen(
            'cat /sys/class/sunxi_info/sys_info | grep "serial"'
        ).readline()

        match = re.search(
            r'sunxi_serial\s*:\s*([a-f0-9]+)',
            id_get
        )

        if match:
            chip_id = match.group(1)
        else:
            print('No chip_id found')

        os_version_get = os.popen(
            'cat /etc/WalnutPi-release | grep "version="'
        ).readline()

        match = re.search(
            r'version=(.*)',
            os_version_get
        )

        if match:
            os_version = match.group(1)
        else:
            print('No os version found')

        os_type_get = os.popen(
            'cat /etc/WalnutPi-release | grep "os_type="'
        ).readline()

        match = re.search(
            r'os_type=(.*)',
            os_type_get
        )

        if match:
            os_type = match.group(1)
        else:
            print('No os type found')

    return chip_platform, chip_id, os_version, os_type


SERVER_IP = 'map.walnutpi.com'
SERVER_PORT = 10240

chip_id = None

while chip_id is None:
    try:
        (
            chip_platform,
            chip_id,
            os_version,
            os_type
        ) = chip_info_get()

    except Exception as e:
        print(f'chip_info_get error: {e}')
        time.sleep(1)

chip_info = {
    'chip_platform': chip_platform,
    'chip_id': chip_id,
    'os_version': os_version,
    'os_type': os_type
}

chip_info_str = json.dumps(chip_info)


def send_message():
    while True:
        try:
            with socket.socket(
                socket.AF_INET,
                socket.SOCK_STREAM
            ) as s:

                s.connect((SERVER_IP, SERVER_PORT))

                s.sendall(
                    chip_info_str.encode('utf-8')
                )

                print(f'Sent: {chip_info_str}')

        except ConnectionRefusedError:
            print(
                'Connection refused. Server might not be running '
                'or IP/Port is incorrect.'
            )

        except Exception as e:
            print(f'An error occurred: {e}')

        time.sleep(300)


thread = threading.Thread(
    target=send_message
)

thread.daemon = True
thread.start()


try:
    while True:
        time.sleep(1)

except KeyboardInterrupt:
    print('Stopped by the user.')
```
