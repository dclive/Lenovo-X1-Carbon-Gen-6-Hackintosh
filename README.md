# Lenovo-X1-Carbon-Gen-6-Hackintosh
Based on Tyler Nguyen's work, this is his X1C6 EFI with a few additions for OC87, this EFI will permit boot of Ventura 13.1 (nothing older is tested) on a Lenovo X1 Carbon Gen 6 (BIOS 1.58, no earlier BIOS is tested).

First, let's be perfectly clear:  Tyler did 99.99% of the work - the hard part.  This exists because of his work.  I'm testing with Ventura, I'm testing with OC87, and I'm testing with some more kexts, and I'm applying a few of my updates.  That's it.  The development, the ACPI stuff, the difficult stuff - that's ALL TYLER.  To see the master at work, hop over to his repository https://github.com/tylernguyen/x1c6-hackintosh and his own site https://tylernguyen.github.io/x1c6-hackintosh/.  

Again, Tyler's work.  I'm updating a few things for my convenience, and sharing it to others.  That's it.  If you want to buy someone a coffee, make sure it's Tyler; he's awesome! 

I've made a few changes, though: 

I set ShowPicker to Yes (hence it's present in the EFI on this page) 

I copied the "Vanilla" BIOS settings to the EFI (so it's present in the EFI on this page); no X1C6 BIOS mods are required

I set SecureBootModel to Disabled in OCAT (so it's present... - imagine that's said for all the other bullet points) 

I set ScanPolicy to Zero so all OSs will be found (take a second longer to scan; no issue for me) 

I updated to OpenCore 87, the latest at this time, plus all associated KEXTs that OCAT (OpenCore Aux Tools) could update

I updated YogaSMC to 1.53, the latest at this time

I added the Ventura version of the pre-release airportintlwlm 2.2 (not enabled; you'd use this if you use an Intel card) 

I added a few kexts to clean up Broadcom wireless, for my Broadcom DW1830.  BT is a WIP; more news in the coming days.  But in Kernel/Quirks I enabled ExtendBTFeatureFlags to hopefully make the BT stuff a bit more compatible with Apple's fancy BT features, once I do get BT working.

Do re-read the above two items; if you replaced your Intel 8265 card with a Broadcom DW1830 card, you may be fully ready to go [you'll use only 2 of the 3 antenna leads on the DW1830); if you still have the Intel card in there, disable the Broadcom items and enable the Intel airportitwlm item, version 2.2 or later for Ventura.

I added alcid=21 to the boot args in NVRAM and updated AppleALC to 1.77 so it's compatible with Ventura

I added 2 .efi drivers so that you can easily add a Linux partition, install (modernLinux) onto the partition, and it will work fine and boot straight from OpenCore.  That said, using the Lenovo EFI boot manager to boot into Linux directly is likely best-practice, since it's not going through any OpenCore-based ACPI or USB, etc. changes.  Same thought process for Windows boot - go directly to Windows Boot Manager, skip OpenCore when using those two OSs if you can.

Oh, and I added some more logging, so it's not quite as pretty when it boots up.  This helps a newbie in understanding what might be causing the crashing.  To disable this, go to https://dortania.github.io/OpenCore-Post-Install/cosmetic/verbose.html

And the keyboard in OC now works after the first boot.  Previously, with OC83 and associated kexts, on the first bootup, the keyboard worked, and then after that, it didn't.  Now, with OC87, it works after each reboot. 

Note:  Update your X1C6 firmwares.  Lenovo's Vantage scanners will not pick up all the updates, like Intel ME.  I had to get Linux fwupdmgr to handle the additional firmwares Windows wouldn't; three minutes spent in Ubuntu 22.10, one five minute reboot, and it was done.  Ubuntu, incidently, finds all hardware perfectly, including both Intel 8265 wifi and DW1830 wifi.  X1C6 BIOS 1.58 is current (and what's tested) at this time.

Download as you wish.  

**New Notes:  (The EFI is the same, OC87)**

**Jan 2, 2023:**  OC88 works; use OCAT to update if you wish.  On first boot, it crashes with ACPI errors.  Poweroff the X1C6 and then power it back on and boot again with OC88; it will work fine from then onward.  Still testing OC88, but it's expected to work great.  Also, in OCAT, change the load order of PatchRam3 to be last in load order (and BCRCMFirmwareData to be before PatchRam3) and those two kexts can be freely enabled.  Bluetooth, however, still doesn't work reliably for me with a DW1830 in the machine.  Still investigating BT.  **After updating to OC88, I'm not seeing the same sleep consistency (ie it's not working as well) as before. Must investigate.**

