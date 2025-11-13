# NVMeG4-IP with DMA on PetaLinux Demo

## Overview
This document provides comprehensive instructions for demonstrating high-speed DMA data transfers between an NVMe Gen4 SSD and main memory using the NVMeG4-IP core on a PetaLinux-based FPGA demo from Design Gateway - **DG NVMeG4-IP PetaLinux demo**.

![Block Diagram](docs/NVMeG4-IP-PetaLinux.png)

## Introduction
The NVMeG4-IP with DMA on PetaLinux demo showcases FPGA-based acceleration for high-speed NVMe Gen4 SSD access.
By offloading data transfer to a dedicated DMA engine, it achieves up to 6900 MB/s write and 7500 MB/s read, minimizing CPU load while demonstrating true Gen4 performance on an embedded Linux platform.

## Comparison: Traditional NVMe Driver vs DG NVMeG4-IP Driver on PetaLinux 
| Feature | Traditional NVMe on PetaLinux | DG NVMeG4-IP with DMA on PetaLinux |
|--------|---------------------------------------------------------|------------------------------------|
| **PCIe Interface** | Uses XDMA + PCIe Hard IP | PCIe Soft IP + Transceivers (No PCIe Hard IP needed) |
| **SSD Support** | NVMe Gen3 SSD | NVMe Gen4 SSD |
| **Typical Performance** | ~2000 MB/s (≈57% of Gen3 SSD max) | ~7000 MB/s (Near full Gen4 performance) |
| **CPU Usage** | High — driver handles protocol in software | Very Low — full NVMe protocol offloaded to hardware |
| **Data Path** | Software-driven NVMe stack | DMA-based, hardware-accelerated datapath |
| **Use Case Fit** | General-purpose NVMe access | High-performance embedded storage acceleration |

## Key Features:
- **High-Bandwidth Data Transfer:**  
  Achieve up to **7 GB/sec** throughput, ideal for data-intensive applications.

- **Unique Solution on Zynq UltraScale+:**  
  The **NVMeG4 IP** core is the only solution delivering this level of NVMe Gen4 performance on Zynq UltraScale+ devices.

- **Seamless Integration with PetaLinux:**  
  Simplifies development and deployment with fully integrated **PetaLinux** driver support.

## About This Demo
This demo runs Design Gateway’s **NVMeG4-IP** with DMA on **PetaLinux**, booted from an SD card and controlled via serial console.
Using the **dgnvme** application, users can execute NVMe commands such as Identify, Write, Read, and SMART to evaluate real-time throughput and reliability of FPGA-driven DMA transfers.

### Resources
- Detailed demo instruction of the DG NVMeG4-IP PetaLinux demo: [Demo Instruction Document](https://dgway.com/products/IP/NVMe-IP/NVMeG4IP-dmalinux-instruction-amd/)
- Detailed reference design of the DG NVMeG4-IP PetaLinux demo: [Reference Design Document](https://dgway.com/products/IP/NVMe-IP/NVMeG4IP-dmalinux-refdesign-amd/)
- Detailed datasheet of the NVMeG4-IP: [Datasheet](https://dgway.com/products/IP/NVMe-IP/dg_nvmeg4_ip_data_sheet_xilinx_en/)

### Test Environment
The demo runs on a PetaLinux-based FPGA system equipped with an NVMe Gen4 SSD. Here are the required components:
1. FPGA development board: ZCU106
2. PCIe adapter board: [AB17-M2FMC](https://dgway.com/ABseries_E.html)
3. SD Card
4. Serial Console

### Running the Demo
1. Boot the FPGA board from SD card and log in with
	```bash
   Login:		root
   Password:	root
2. Verify the driver and device with **lsmod** and **ls /dev/dgnvme\***.
3. Launch the application using **dgnvme**.

## Demo Download
1. Demo Configuration files: Request via the [demo inquiry form](https://dgway.com/download/download_form.html?d=NVMeG4IP_dmalinux_ZCU106.zip).
2. For more information, please visit Design Gateway’s Storage IP Cores for AMD: [Visit Here](https://dgway.com/en/amd/storage-ip-cores.html).

## Watch the Demo on YouTube

[![Watch on YouTube](https://img.youtube.com/vi/OREg36v9Oaw/0.jpg)](https://youtu.be/OREg36v9Oaw)

---

Feel free to explore and contribute to this repository for improvements and enhancements to the NVMeG4-IP PetaLinux demo.
