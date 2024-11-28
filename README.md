# How to get Fenvi T919 to work in Sonoma or Sequoia

### If you want to know more about Broadcom wifi cards, check <a href="https://github.com/perez987/Broadcom-wifi-back-on-macOS-Sonoma-with-OCLP/tree/main">perez987</a> github.

I want to make an easy and fast tutorial to make Wifi and Bluetooth work in Sonoma and Sequoia with Fenvi T919 card in a few steps.

## Tutorial

You need:
- <a href="https://github.com/dortania/OpenCore-Legacy-Patcher/tree/main/payloads/Kexts/Wifi" target="_blank" rel="noopener noreferrer">IOSkywalkFamily.kext</a>
- <a href="https://github.com/dortania/OpenCore-Legacy-Patcher/tree/main/payloads/Kexts/Wifi" target="_blank" rel="noopener noreferrer">IO80211FamilyLegacy.kext</a>
- <a href="https://mackie100projects.altervista.org/opencore-configurator/" target="_blank" rel="noopener noreferrer">OpenCore Config</a>
- <a href="https://github.com/dortania/OpenCore-Legacy-Patcher/releases" target="_blank" rel="noopener noreferrer">OpenCore Legacy Patcher</a>

Then:
- Download `IOSkywalkFamily.kext` and `IO80211FamilyLegacy.kext` and place it in your `Kexts` folder
- Open your `config.plist` in OpenCore Config and go to your `Kernel` tab
- Click on `Scan/Browse` to add the new Kexts in your config.plist
- Place the Kexts in the right order like shown and set `MinKernel` to `23.0.0`
<img width="750" alt="Capture d’écran 2024-11-28 à 12 38 59" src="https://github.com/user-attachments/assets/bf0f4e10-d8d7-4a8d-9f8b-a3163faa251c">

- Go to the `Block` which is on top and add `com.apple.iokit.IOSkywalkFamily`, set `MinKernel` to `23.0.0` and set `Strategy` to `Exclude`
<img width="750" alt="Capture d’écran 2024-11-28 à 12 56 39" src="https://github.com/user-attachments/assets/c487317c-a10c-4b23-b634-8e02b36fe24a">

- Go to the `MISC` tab then to `Security` on top and choose `Disabled` in `SecureBootModel`
<img width="750" alt="Capture d’écran 2024-11-28 à 13 00 31" src="https://github.com/user-attachments/assets/410d051a-f264-43a9-bf0b-10fe11b945c3">

- Go to the `NVRAM` tab then add to boot-args `amfi=0x80` and csr-active-config to `03080000`
<img width="750" alt="Capture d’écran 2024-11-28 à 13 05 07" src="https://github.com/user-attachments/assets/1045b441-a5db-47f7-b81f-010433078dd6">

- Now quit OpenCore Config and save the changes and eject EFI
- `Reset NVRAM` while rebooting your PC
- After reboot, open OpenCore Legacy Patcher and click on `Post-Install Root Patch` and then on `Start Root Patching`
- When finished, `Reset NVRAM` while rebooting your PC


### Your Wifi and Bluetooth should work perfectly now

<img width="400" alt="Capture d’écran 2024-11-28 à 13 14 15" src="https://github.com/user-attachments/assets/be6e7d49-67dc-4073-8d24-09175fad166f">
