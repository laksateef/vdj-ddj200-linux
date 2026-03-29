# VirtualDJ Mapping for Pioneer DDJ-200 on Linux

This project provides working configuration files to use the Pioneer DDJ-200 MIDI controller with VirtualDJ software, running via Wine (using Bottles) on a Linux operating system.

The goal is to offer a simple setup and avoid the long hours of troubleshooting encountered during setup on Bazzite.

## Context

This configuration was successfully tested on:
- **OS:** Bazzite (Fedora-based Linux)
- **Software:** VirtualDJ 2025 (b8472) installed via **Bottles** (Flatpak)
- **Controller:** Pioneer DDJ-200 (connected via USB)

## Installation

1.  **Download the files from this repository.**
    You can clone the repository or download the `SIMPLE_MIDI_0_0.xml` files individually:
    - The file in the `devices/` folder
    - The file in the `mappers/` folder

2.  **Place the files in the VirtualDJ folders.**
    Copy each file into the corresponding folder inside your Wine "bottle". Replace `[YOUR_BOTTLE]` with your actual bottle name:

    - **Device File:**
      Copy `devices/SIMPLE_MIDI_0_0.xml` to:
      `~/.var/app/com.usebottles.bottles/data/bottles/[YOUR_BOTTLE]/drive_c/users/steamuser/AppData/Local/VirtualDJ/Devices/`

    - **Mapper File:**
      Copy `mappers/SIMPLE_MIDI_0_0.xml` to:
      `~/.var/app/com.usebottles.bottles/data/bottles/[YOUR_BOTTLE]/drive_c/users/steamuser/AppData/Local/VirtualDJ/Mappers/`

## Required Configuration

### 1. Flatpak Permissions for Bottles
Bottles needs permission to access your USB hardware.
* **Via Flatseal:** Select **Bottles**, go to the `Filesystem` section and enable `All system devices`.
* **Via Terminal:**
    ```bash
    flatpak override --user --device=all com.usebottles.bottles
    ```

> [!IMPORTANT]
> **Custom Pad & Shift Behavior**
> This configuration is heavily customized for a **Stems and Loops** workflow. It deviates from the factory default:
> * **Performance Pads:** Hardcoded to **Stems** (Mute/Unmute Vocal, Instru, Bass, etc.) instead of Sampler or Hot Cues.
> * **SHIFT + Pads:** Mapped to **Auto Loops** (8, 16, 32, 64 beats). They do NOT trigger the default secondary actions.
>
> If you need the Sampler or standard Hot Cues, this mapping is not suitable without manual XML modification.
>
> **MIDI Documentation:** [DDJ-200 MIDI Message List](https://downloads.support.alphatheta.com/software_info/dj-controllers/DDJ-200/DDJ-200_MIDI_Message_List_E2.pdf)

### 2. Setup VirtualDJ

1.  To prevent the interface from flickering under Wine : launch VirtualDJ -> **Settings** -> **OPTIONS**.
2.  Search for `experimentalSkinEngine`.
3.  Set it to **No**.
4.  Don't forget to select the SIMPLE_MIDI_0_0 file in the controller mapping
<p align="center"> <img src="https://github.com/user-attachments/assets/af6e3027-f87f-40d6-a3d1-c5dbb870b274" width="600" title="VirtualDJ Settings"> </p>

## Mapping Details

| Physical Control | VDJ Action |
|---|---|
| PLAY / PAUSE | `play_pause` (LED feedback included) |
| CUE | `cue_stop` |
| SYNC | `sync` |
| SHIFT + SYNC | Reset pitch (`pitch_reset`) |
| PFL (Headphone) | `pfl` (pre-listening) |
| SHIFT + PFL | Load selected track (`load`) |
| JOGWHEEL (Top) | Scratch (`touchwheel`) |
| JOGWHEEL (Side) | Bend (`jogwheel`) |
| SHIFT + JOGWHEEL (Side) | Browse library (`browser_scroll`) |
| PADS 1-3 | Mute Stems (Vocal, Instrumental, Bass) |
| PADS 5-6 | Mute Stems (Kick, Hihat) |
| SHIFT + PADS 1-4 | Auto Loops (8, 16, 32, 64 beats) |# VirtualDJ Mapping for Pioneer DDJ-200 on Linux
