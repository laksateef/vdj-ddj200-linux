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

### 2. Graphics Fix (Flickering)
To prevent the interface from flickering under Wine:
1.  Launch VirtualDJ -> **Settings** -> **OPTIONS**.
2.  Search for `experimentalSkinEngine`.
3.  Set it to **No**.

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

This project provides working configuration files to use the Pioneer DDJ-200 MIDI controller with VirtualDJ software, running via Wine (using Bottles) on a Linux operating system.

The goal is to offer a simple setup and avoid the long hours of troubleshooting that I personally encountered.

## Context

This configuration was successfully tested on:
- **OS:** Bazzite (a Fedora Linux derivative)
- **Software:** VirtualDJ 2025 (b8472) installed via **Bottles** (Flatpak)
- **Controller:** Pioneer DDJ-200 (connected via USB)

## Installation

1.  **Download the files from this repository.**
    You can either clone the repository or download the `SIMPLE_MIDI_0_0.xml` files individually:
    - The file in the `devices/` folder
    - The file in the `mappers/` folder

2.  **Place the files in the VirtualDJ folders.**
    You need to copy each file into the corresponding folder inside your Wine "bottle" where VirtualDJ is installed. The path looks like this:

    - **Device File:**
      Copy `devices/SIMPLE_MIDI_0_0.xml` to:
      `~/.var/app/com.usebottles.bottles/data/bottles/bottles/VDJ/drive_c/users/steamuser/AppData/Local/VirtualDJ/Devices/SIMPLE_MIDI_0_0.xml`

    - **Mapper File:**
      Copy `mappers/SIMPLE_MIDI_0_0.xml` to:
      `~/.var/app/com.usebottles.bottles/data/bottles/bottles/VDJ/drive_c/users/steamuser/AppData/Local/VirtualDJ/Mappers/SIMPLE_MIDI_0_0.xml`

    > **Note:** The path might vary slightly (`VDJ`, `steamuser`, etc.) depending on your Bottle's name and your username.

## Required Configuration

For everything to work correctly, two crucial steps are necessary:

### 1. Flatpak Permissions for Bottles

The Bottles application needs to access your MIDI controller.
1.  Install **Flatseal** (available on Flathub/Software Center).
2.  Launch Flatseal and select **Bottles** from the application list.
3.  Go to the `Filesystem` section and enable the `All system devices` option. This allows Bottles to see the DDJ-200.
    ![image](https://github.com/laksateef/vdj-ddj200-linux/assets/166160569/341f2343-e380-4592-86cd-d883b063857d)


### 2. Setting in VirtualDJ

A known issue can cause the VirtualDJ interface to flicker or blink when running under Wine.
1.  Launch VirtualDJ.
2.  Go to **Settings** -> **OPTIONS**.
3.  Use the search bar to find the `experimentalSkinEngine` option.
4.  Set this option to **No**.

## Mapping Details

This mapping is designed to be both simple and functional, making good use of the DDJ-200's features.

| Physical Control | VDJ Action |
|---|---|
| PLAY / PAUSE | `play_pause` (LED blinks when paused) |
| CUE | `cue_stop` |
| SYNC | `sync` |
| SHIFT + SYNC | Reset pitch (`pitch_reset`) |
| PFL (Headphone) | `pfl` (activates pre-listening for the deck) |
| SHIFT + PFL | Load selected track (`load`) |
| JOGWHEEL (Top) | Scratch (`touchwheel`) |
| JOGWHEEL (Side) | Bend (`jogwheel`) |
| SHIFT + JOGWHEEL (Side) | Browse library (`browser_scroll`) |
| PADS 1-3 | Mute Stems (Vocal, Instrumental, Bass) |
| PADS 5-6 | Mute Stems (Kick, Hihat) |
| SHIFT + PADS 1-4 | Auto Loops (8, 16, 32, 64 beats) |

---

