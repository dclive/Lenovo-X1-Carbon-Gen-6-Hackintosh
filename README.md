# X1C6-Hack
Based on Tyler Nguyen's work, this is his X1C6 EFI with a few additions for OC87

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

I added a few kexts to clean up Broadcom wireless, for my Broadcom DW1830.  BT is a WIP; more news in the coming days.

I added ALC=21 to the boot args in NVRAM and updated AppleALC to 1.77 so it's compatible with Ventura

I added 2 .efi drivers so that you can easily add a Linux partition, install (modernLinux) onto the partition, and it will work fine and boot straight from OpenCore.  You might have to play with boot order in BIOS a bit, but the objective is OpenCore first.  

Oh, and I added some more logging, so it's not quite as pretty when it boots up.  This helps a newbie in understanding what might be causing the crashing.  To disable this, go to https://dortania.github.io/OpenCore-Post-Install/cosmetic/verbose.html

And the keyboard in OC now works after the first boot.  Previously, with OC83 and associated kexts, on the first bootup, the keyboard worked, and then after that, it didn't.  Now, with OC87, it works after each reboot. 

Note:  Update your X1C6 firmwares.  Lenovo's Vantage scanners will not pick up all the updates, like Intel ME.  I had to get Linux fwupdmgr to handle the additional firmwares Windows wouldn't; three minutes spent in Ubuntu 22.10 and it was done.  Ubuntu, incidently, finds all hardware perfectly, including both Intel 8265 wifi and DW1830 wifi.  X1C6 BIOS 1.59 is current (and what's tested) at this time; use it.

Download as you wish.  
