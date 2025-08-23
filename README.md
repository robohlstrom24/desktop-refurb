# Project Overview
This project involved refurbishing a Dell OptiPlex 5060 SFF desktop to demonstrate CompTIA A+ core skills by improving system specifications. After a clean installation of Windows 11, the system was enhanced with upgraded RAM, expanded storage, and a WiFi/Bluetooth card. The upgraded components were configured and performance improvements were validated with PowerShell benchmarks. Troubleshooting activities were documented in a companion repository [link]. 

## Hardware Specifications

### Stock Configuration
| Component | Details                                                                 |
|-----------|-------------------------------------------------------------------------|
| CPU       | Intel Core i5-8500 @ 3.00 GHz (6 cores, Coffee Lake, LGA1151 socket)    |
| RAM       | 16 GB DDR4 (2×8 GB, 2666 MHz, non-ECC UDIMM; 4 slots total, 64 GB max)  |
| Storage   | Samsung 256 GB M.2 SATA SSD                                             |
| Graphics  | Intel UHD Graphics 630 (integrated, no GPU)                             |
| Wireless  | None (no WiFi/Bluetooth card)                                           |
| Chipset   | Intel Q370                                                              |

### Upgrades
| Component         | Details                                                          |
|-------------------|------------------------------------------------------------------|
| RAM               | OWC 32 GB DDR4 (2×16 GB, 2666 MHz) non-ECC UDIMM                 |
| Storage           | Western Digital SN770 1 TB, M.2 NVMe SSD                         |
| WiFi/Bluetooth    | TP-Link WiFi 6E Intel AX210 PCIe, Bluetooth 5.3, WPA3 security   |

## Action steps

### Windows 11 installation on stock SSD

1. Verified SSD detected in BIOS
2. Verified SATA operation mode set to AHCI 
3. Verified Secure Boot was enabled (Legacy Option ROMs disabled)
4. Booted from Windows 11 installation media
5. Resolved partition selection error during install (see Troubleshooting Journal repo, ticket T-0003 [link])
6. Completed clean installation of Windows 11 on stock SSD; system booted successfully

### RAM upgrade

1. Performed PowerShell compute benchmark on stock 2x8 GB RAM (square integers 1 through 1,000,000; result 2.41 seconds)
2. Removed stock 2x8GB DDR4 RAM
3. Installed Crucial 2x16 GB DDR4 RAM and booted into BIOS to confirm specifications
4. Observed BIOS was misreporting each Crucial module as 8 GB
5. Verified system incompatibility with Crucial RAM (see Troubleshooting Journal repo, ticket T-0004 [link])
6. Ordered and installed OWC 2x16 GB RAM 
7. Verified 32 GB RAM recognized in BIOS
8. Performed the same PowerShell compute benchmark on newly installed RAM (result 1.06 seconds)
- Note: Benchmark script adapted from reference code 
- Upgrade produced ~2.5x speed increase compared to stock configuration

<img width="277" height="196" alt="RAM 1" src="https://github.com/user-attachments/assets/9d163b8e-d94d-4aa4-8bd5-b0e1c0aac68d" />

Stock 2x8 GB RAM modules (right) and upgraded 2x16 GB RAM modules (left)

<img width="290" height="248" alt="RAM 2" src="https://github.com/user-attachments/assets/e9d43a42-9f23-4d52-8e8b-c5ed20180e1b" />

Seating 16 GB RAM module into DIMM slot 1

### SSD Upgrade

1. Performed PowerShell read/write performance test on stock Samsung 256 GB M.2 SATA SSD (stopwatch + file I/O with byte arrays; 512 MB test file. Results: 2.63 seconds read, 0.31 seconds write)
2. Removed stock SSD and installed WD SN770 1 TB M.2 NVMe PCIe SSD in the same M.2 slot
3. Resolved boot issue (blank screen after Dell splash) by correcting BIOS date/time and replacing CMOS battery (see Troubleshooting Journal repo, ticket T-0005 [link])
4. Verified drive detected as NVMe PCIe in BIOS
5. Performed clean Windows 11 installation and validated successful boot
6. Performed the same PowerShell read/write performance test on upgraded SSD (Results: 0.50 seconds read, 0.17 seconds write)
- Note: benchmark script adapted from reference code
- Upgrade produced  ~5x improvement in read performance, ~2x improvement in write performance
  
<img width="273" height="214" alt="SSD 1" src="https://github.com/user-attachments/assets/de694fc7-f760-4a2b-aed2-954e4a6ef3f4" />

Stock SATA SSD (top) and upgraded NVMe SSD (bottom)

<img width="291" height="352" alt="SSD 2" src="https://github.com/user-attachments/assets/bf4d49b3-336d-41c0-82ae-8544adbcb057" />

Removing 256 GB SATA SSD from motherboard M.2 slot

### WiFi/Bluetooth card install

1. Installed TP-Link WiFi/Bluetooth card into PCIe x1 slot, removing case slot cover for rear access
2. Resolved compatibility issue (no available USB port on motherboard) with adapter cable (9-pin USB header to USB Type-A)
3. Booted system and verified both WiFi and Bluetooth were detected and functional
4. Installed latest Intel AX210 WiFi and Bluetooth drivers for security

<img width="320" height="331" alt="WiFi 1" src="https://github.com/user-attachments/assets/640c5ba5-5108-4416-b856-16050eaad0c1" />

Seating WiFi/Bluetooth card in PCIe x1 slot

<img width="232" height="539" alt="WiFi 2" src="https://github.com/user-attachments/assets/19fbd2b1-1d23-4a5e-8d26-bbfd8a922e5e" />

Adapter cable workaround enabling Bluetooth connectivity
