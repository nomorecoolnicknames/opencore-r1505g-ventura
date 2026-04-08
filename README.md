# AMD Ryzen Embedded R1505G - OpenCore EFI

<img align="right" src="https://4pda.to/s/HEBh3c3MDjxJ9fr663k25iHIYYcgX3oyjOOqKuOeJz0Y.png" alt="Mini-PC with Ryzen Embedded R1505G" width="280">

[![macOS](https://img.shields.io/badge/macOS-13.6.3-brightgreen.svg)](https://support.apple.com/)
[![OpenCore](https://img.shields.io/badge/OpenCore-Ventura-blue.svg)](https://github.com/acidanthera/OpenCorePkg)
[![AMD](https://img.shields.io/badge/Platform-AMD_R1505G-red.svg)](https://github.com/AMD-OSX/AMD_Vanilla)

**Disclaimer**  
This EFI is made for my exact mini-PC and is shared as a reference build.  
Use your own SMBIOS values before booting.

Target device:

- `QBiP-1605B (GB-BSRE-1605, MRZNRNS)`
- industrial compact SBC by `GIGAIPC` (a `GIGABYTE` sub-brand)

&nbsp;

## Hardware

| Category | Component |
| -------- | --------- |
| CPU | AMD Ryzen Embedded R1505G |
| iGPU | Radeon Vega 3 |
| Device | QBiP-1605B / GB-BSRE-1605 / MRZNRNS |
| Memory | 8GB DDR4 2400 |
| SSD | SATA SSD 256GB |
| macOS | Ventura 13.6.3 |
| SMBIOS | iMacPro1,1 |
| SATA AHCI | AMD `1022:7901` |

&nbsp;

## Status

<details>
<summary><strong>Working</strong></summary>
<br>

- [x] macOS Ventura 13.6.3 boot
- [x] Installer boot
- [x] NootedRed graphics acceleration
- [x] USB via `USBToolBox.kext + UTBMap.kext`
- [x] SATA AHCI `1022:7901` via `AMDSata.kext`
- [x] OpenCanopy picker

</details>

<details>
<summary><strong>Not tested</strong></summary>
<br>

- [ ] Ethernet port #1
- [ ] Ethernet port #2
- [ ] audio layout tuning on other board revisions
- [ ] sleep / wake long-term behavior
- [ ] iServices after replacing placeholder SMBIOS

</details>

<details>
<summary><strong>Included</strong></summary>
<br>

- `SSDT-EC-USBX-DESKTOP.aml`
- `OpenRuntime.efi`
- `OpenHfsPlus.efi`
- `OpenCanopy.efi`
- `Lilu.kext`
- `VirtualSMC.kext`
- `AppleALC.kext`
- `RealtekRTL8111.kext`
- `NootedRed.kext`
- `NVMeFix.kext`
- `USBToolBox.kext`
- `UTBMap.kext`
- `AMDSata.kext`
- `AppleMCEReporterDisabler.kext`

</details>

<details>
<summary><strong>Before booting</strong></summary>
<br>

- Replace `SystemSerialNumber`
- Replace `MLB`
- Replace `SystemUUID`
- Replace `ROM`
- BIOS: `UEFI Only`, `Secure Boot Off`, `Fast Boot Off`, `CSM Off`, `SATA AHCI`

</details>

&nbsp;

## Notes

- `UTBMap.kext` is specific to this machine.
- This is not a universal EFI for all Ryzen mini-PCs.
- Current boot-args: `-v debug=0x100 keepsyms=1 npci=0x2000`
- Two onboard Ethernet ports are present on the device, but neither was verified yet.
- Some functions may still require extra tuning depending on BIOS version and board revision.
