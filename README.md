# EFI DELL G15 - 5515 (Ryzen Edition)

## Attetion
I recommend keeping Windows on Dual-Boot, we have kexts in beta, we don't know when a break in compatibility may occur.

I am not responsible for loss of data, nuclear war, damage to peripherals or if your laptop explodes. We are dealing with hackintosh, itself is an experimental method, be aware of the possible problems that may occur and research before trying to install. Know what you are dealing with.

I generated the EFI based on my CPU, it may be necessary to change some fields in your config.plist, to generate them you will need Gen-SM-Bios (link: https://github.com/corpnewt/GenSMBIOS), the fields to be changed are in Root/PlataformInfo and are:
* SystemSerialNumber ('Serial' value generated by SM-BIOS)
* MLB ('Board Serial' value generated by SM-BIOS)
* SystemUUID ('SmUUID' value generated by SM-BIOS)
* ROM ('Apple ROM' value generated by SM-BIOS)

## Video
Attention: this EFI uses NottedRed for APU VIDEO.
The Dell G15 5515 has the GeForce RTX3050 video card, currently this card is not compatible with Mac OS and I am not aware of any project to implement compatibility with this card.

So, the only possibility is to use the AMD APU video, but I couldn't allocate more than 512mb of VRAM, if anyone can, feel free to make a pull request.

NottedRed is an experimental Kext, it is in the beta phase, it can bring some instabilities to your hackintosh video, for example, crashes in some programs (mainly in Google Chrome, I recommend using Safari).

## OS X
I used this EFI to install Monterey, I was unsuccessful in installing Ventura and when updating through OS X itself I was unsuccessful.

## Instructions
To install Monterey, I recommend downloading the installation image using mac recovery method, more details in this (link: https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install-recovery.html)

When starting the installation wizard with kexts enabled, you will need them to use wireless, mouse and keyboard.

After downloading the installation image you must wait for the mac to restart, when the installation starts you will be stuck on the apple screen, this is due to some Kexts, to solve the error, have a computer or system available to edit plist (if using windows I recommend proppertree).

Using PropperTree or other plist file editing software, disable the Kexts:
* VoodooPS2Keyboard
* VoodooPS2Mouse
* VoodooPS2Trackpad
* VoodooPS2Controller
* VoodooI2CSynaptics

I recommend that you pass the '-v' flag in the boot-args, so you can see the installation process and if any errors occurred, note, when I installed there were some errors, including some that took a long time to exit, this is normal, be patient , however if you see that you haven't left a line for more than 25 minutes, then something has probably gone wrong.

Restart the macOS installation.

After installation you will need the peripherals, edit the config.plist again enabling the kexts that you disabled in the previous step.

That's it, your hackintosh should be functional, copy the EFI from the pendrive to the HD and configure the EFI boot in the BIOS (Warning, be careful in this step, never delete files without knowing what you are doing, this could break the EFI boot. There are videos on youtube that can help you with this step.)
