# ZX-EQ Nemo-bus Edition (Universal CPLD)

## Spectrolyzer Cartridge for ZX Spectrum. Based on the RBSC architecture.

> [English](README.en.md) | [Русский](README.md)  

**ZX-EQ** is a hardware audio spectrum analyzer (expansion cartridge) designed for the ZX Spectrum computer family, heavily inspired by the original hardware design developed by the **RBSC** team. The device visualizes music frequencies and notes in real time during games and demo-scene playbacks using multi-segment LED bars.

The core processor of the cartridge is an Altera/Intel MAX CPLD chip housed in a **TQFP-100** package.

*Important Note:* This repository is based on the official RBSC/ZX-EQ project documentation. All enhancements, structural modifications, and edge-connector changes have been executed with strict respect to the original authors.

***

## Key Hardware Upgrades

1. **Nemo-bus Form Factor:** The printed circuit board is designed to plug directly into the standard Nemo-bus expansion slots found on modern clones and upgraded vintage motherboards (such as the ZX-Evolution, Scorpion ZS-256, Kay, and ZXM-Phoenix).
2. **Multi-CPLD Architecture:** The PCB power distribution lines and logic paths have been redesigned to be multi-voltage tolerant. This allows you to choose between two different generations of Altera/Intel CPLD chips in the TQFP-100 package:
    *   **Altera MAX 7000S:** EPM7128STC100 / EPM7160STC100 (Native +5V core logic).
    *   **Altera MAX 3000A:** EPM3128ATC100 (+3.3V core logic, featuring 5V-tolerant input pins perfectly safe for the Nemo-bus lines).

***

## Bill of Materials (BOM) & Jumper Configuration

Depending on which CPLD chip family you choose to solder, you must adjust the onboard power circuitry configuration:

### Option A: Using the EPM3128ATC100 (+3.3V CPLD)
*   **Voltage Regulator:** You **MUST** solder a 3.3V LDO regulator chip (such as the LT1117-3.3) onto the board to feed the low-voltage CPLD core.
*   **Power Jumper (JP1):** Must be left completely **OPEN** (un-soldered).
*   **Firmware:** Use a `.pof` or `.jed` binary compiled specifically for the MAX3000A family.

### Option B: Using the EPM7128STC100 / EPM7160STC100 (+5V CPLD)
*   **Voltage Regulator:** Not required. You can safely skip soldering the LDO regulator along with its input/output filter capacitors `C3` and `C4`.
*   **Power Jumper (JP1):** Must be **SHORTED** (soldered closed) to route raw 5V power straight to the CPLD power pins.
*   **Firmware:** Flash the original RBSC `.pof` binary compiled for the MAX7000S family.

***

## CPLD Firmware Programming

Thanks to the universal power distribution layout, this project natively supports firmware code targeting different Altera/Intel CPLD generations. 

This repository includes custom modifications and provides full, seamless integration with the **alternative firmware repository by andykarpov (zx-eq-firmware)**. This third-party code branch vastly broadens the choice of compatible LED bar components and pin polarities.

### Available Firmware Binaries
Please browse the [/Firmware](https://github.com/Alex-2-Graf/ZX-EQ) folder of this repository. Select the specific `.pof`/`.jed` file that exactly matches your soldered CPLD model, your specific LED segment bar configuration, and desired polarity.

### JTAG Programming Steps
1. Connect an **Altera USB Blaster** (or equivalent hardware programmer) to the onboard 10-pin JTAG header.
2. Provide power to the cartridge either by plugging it into a powered Nemo-bus slot or using an external +5V desktop power supply.
3. Open the **Quartus Programmer** software tool, scan for the JTAG chain, select your chosen `.pof` file, check the `Program/Configure` option, and press **Start**.

---

## 🎨 Hardware Gallery & PCB Renders

Visual project documentation, high-definition photographs of assembled devices, and 3D PCB renders can be found inside the [/Foto](https://github.com/Alex-2-Graf/ZX-EQ) directory.

---

## 👥 Credits & Acknowledgments

*   **RBSC (Retro-Computers Breeding Society)** — Authors of the original circuit diagram, Core Spectrum analyzer hardware logic, and general cartridge concept.
*   **Andrey Karpov (andykarpov)** — Author of the excellent alternative firmware optimization branch featuring robust 8-bit scale controls and flexible LED pin polarity configuration.

---

## 📜 Disclaimer and Licensing Terms

In absolute accordance with the open-source distribution rules established by the original authors (RBSC):
*   This project files are provided **"AS IS"**, without any warranties of any kind, explicit or implied.
*   ⚠️ **STRICTLY NOT FOR COMMERCIAL USE!** Fabricating a small batch of PCBs and selling the excess unpopulated blank boards to local hobbyists solely to cover your manufacturing costs is perfectly fine. However, any large-scale, automated commercial production or commercial kit distribution **requires explicit, prior written approval** from the RBSC team.
