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
