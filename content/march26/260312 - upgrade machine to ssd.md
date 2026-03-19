## For future reference
- Old SSD: the SAMSUNG 256GB SSD 
- New SSD: the SAMSUNG 990 PRO 2TB M.2 SSD
- Old HDDs: we have 2 TOSHIBA DT01ACA100
## Physical installation
- Installed the new SSD in the M2 slot in the motherboard (see [this video](https://www.youtube.com/watch?v=eVZCwk1THLE&t=102s))
## Clonezilla 
clonezilla log in USB
## Problem: booting into the wrong disk 
- apparent reason: clonezilla clones the UUID so the two drives share the same UUID and BIOS is confused, here it just went with booting up the original drive. There is no multiple options inside BIOS boot (only one Windows Boot Manager entry) 
- solution: followed this guide from [here](https://sourceforge.net/p/clonezilla/discussion/Help/thread/06934286e9/)
> I booted the cloned Windows to the login screen, pressed shift while clicking the power button to the down right and chose restart. This is to get the advanced start settings to be able to enable safe mode. Probably is several solutions for this, but I did it like this and then rebooted.
> 
> Then I started in safe mode with command prompt, logged in and the "unknown hard error" showed. Clicked that away and after a while the command prompt pops up, then start diskpart and list volumes to check what drive letters the disks/volumes have. The original disk/volume will probably still have the C: letter, and this is what you need to change. Check what your cloned disk is mounted as, in my case it was D:.
> 
> Press ctrl+shift+esc to start task manager. Then file menu, run new task and type regedit (the registry editor). Browse to HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices and change/rename the key \DosDevices\C: to some letter not taken, I chosed U:. Then change/rename the cloned drive letter, in my case the \DosDevices\D: to \DosDevices\C:, and that was the trick. Reboot and log in, hopefully everything works. I chosed to disable the original disk in the device manager also. Hop e I don't run in to any other problems, like the Windows update. Time will tell.
> 
> And although I had restored an disk image for this like I wrote in my last post, I believe it would have been the same solution with the drive clone (after fixing the EFI partition) as well.

- problem: we actually cloned (when we cloned md126 to nvme) we cloned the D drive, not the C drive. 
	- should i use another cloning method? 

## Enabling AHCI mode 
Following [this](https://superuser.com/questions/1675984/how-can-i-turn-off-intel-rst-without-losing-all-my-data/1676017#1676017) guide (until step "*- Change the SATA Operation mode to AHCI from either IDE or RAID (again, the language varies).
- Save changes and exit Setup and Windows will automatically boot to Safe Mode.*")

> [!NOTE] shoulda installed AHCI drivers first 
> - in retrospect, i should have installed ahci drivers first (per some reddit comment), maybe the drive wouldn't have been so broken? 
> - aah, didn't i do this in the summer 2025 already, and the drive remained broken? 

## Second Clonezilla clone 
After enabling AHCI mode, clonezilla now recognizes the 256gb disk 
Cloning 
CLONING FAILED! failed to clone last (and main) partition due to "bad sectors" 

perhaps I should try to restart to windows first to enable AHCI drivers or whatever

## Reboot to Windows 

Windows keeps rebooting to advanced control screen

Pulled out power cable and flushed remaining power, restarted 

## DELL Fixing (:\\\\256....) <- drive name screen 
Eventually no new disk activity (disk activity light stopped blinking) and screen is stuck -> I just force shutdown the computer 

## Change to AHCI again, reboot to Windows again
This time everything works! Old SSD and Old HDD #2 ended up needing to be formatted 
- Old SSD: after all, the data is copied to new SSD already. We use clonezilla command shell 
	- `mkfs.ntfs -f /dev/nvme1n1` (-f for quick format)
	- then reformat once again in Windows (after last step, it appears as unallocated)
- Old HDD #2: classic reset in windows diskpart gui. 

---- 
## Other thoughts 
- In the end, i shouldn't clone the original HDD -> original SSD (because SSD are more susceptible to corruption, and it seems it is kinda already corrupted)