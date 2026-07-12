# ZX-EQ Nemo-bus Edition (Universal CPLD)

## Spectrolyzer Cartridge for ZX Spectrum. Based on the RBSC architecture.

> [English](README.en.md) | [Русский](README.md)  

**ZX-EQ** is a hardware audio spectrum analyzer (expansion cartridge) designed for the ZX Spectrum computer family, heavily inspired by the original hardware design developed by the **RBSC** team. The device visualizes music frequencies and notes in real time during games and demo-scene playbacks using multi-segment LED bars.

The core processor of the cartridge is an Altera/Intel MAX CPLD chip housed in a **TQFP-100** package.

*Important Note:* This repository is based on the official [RBSC/ZX-EQ](https://github.com/RBSC/ZX-EQ) project documentation. All enhancements, structural modifications, and edge-connector changes have been executed with strict respect to the original authors.

***

## Key Hardware Upgrades

1. **Nemo-bus Form Factor:** The printed circuit board is designed to plug directly into the standard Nemo-bus expansion slots found on modern clones and upgraded vintage motherboards (such as the ZX-Evolution, Scorpion ZS-256, Kay, and ZXM-Phoenix).
2. **Multi-CPLD:** The board is designed for universal power supply and logic level tolerance. Two types of FPGA chips in TQFP-100 packages are supported:
    *   **Altera MAX 7000S:** EPM7128STC100 / EPM7160STC100.

***

## CPLD Firmware Programming

This repository includes custom modifications and provides full, seamless integration with the **alternative firmware repository by [andykarpov/zx-eq-firmware](https://github.com/andykarpov/zx-eq-firmware)**. This third-party code branch vastly broadens the choice of compatible LED bar components and pin polarities.

### Available Firmware Binaries
Please browse the [/Firmware](Firmware) folder of this repository. Select the specific `.pof`/`.jed` file that exactly matches your soldered CPLD model, your specific LED segment bar configuration, and desired polarity.

### JTAG Programming Steps
1. Connect an **Altera USB Blaster** (or equivalent hardware programmer) to the onboard 10-pin JTAG header.
2. Provide power to the cartridge either by plugging it into a powered Nemo-bus slot or using an external +5V desktop power supply.
3. Open the **Quartus Programmer** software tool, scan for the JTAG chain, select your chosen `.pof` file, check the `Program/Configure` option, and press **Start**.

---

## 🎨 Hardware Gallery & PCB Renders

Visual project documentation, high-definition photographs of assembled devices, and 3D PCB renders can be found inside the [/Foto](Foto) directory.

---

## 👥 Credits & Acknowledgments

*   **RBSC (Retro-Computers Breeding Society)** — Authors of the original circuit diagram, Core Spectrum analyzer hardware logic, and general cartridge concept.
*   **Andrey Karpov (andykarpov)** — Author of the excellent alternative firmware optimization branch featuring robust 8-bit scale controls and flexible LED pin polarity configuration.

---

## 📜 Disclaimer and Licensing Terms

In absolute accordance with the open-source distribution rules established by the original authors (RBSC):
*   This project files are provided **"AS IS"**, without any warranties of any kind, explicit or implied.
*   ⚠️ **STRICTLY NOT FOR COMMERCIAL USE!** Fabricating a small batch of PCBs and selling the excess unpopulated blank boards to local hobbyists solely to cover your manufacturing costs is perfectly fine. However, any large-scale, automated commercial production or commercial kit distribution **requires explicit, prior written approval** from the RBSC team.
