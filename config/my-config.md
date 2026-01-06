# Windows - Config & Deployment

> On a fresh installation of Windows.

---

> Performance: It is recommended after 2.5 years, to make a new user and "move there". [after typical maintenance like clearing cache, etc]

> Performance: It is recommended after 5 years to reinstall the OS.

> Security: Configure firewall for a whitelist.

> Adjust performance settings from Advanced System Settings (right of Right Click Computer, Properties) something panel.

---

## Chocolatey Script

```powershell

## In order of importance and frequency.
## Commands are tested.

choco install veracrypt keepass deluge firefox winrar open-shell powershell-core # powershell 7+
choco install googlechrome hexchat vlc steam libreoffice-fresh
choco install notepadplusplus thunderbird handbrake cherrytree gimp
choco install calibre adobereader 7zip idrive freedownloadmanager

choco install imagemagick caesium.install freemind qtox atom crystaldiskinfo
choco install anki blender inkscape krita audacity obs-studio
choco install virtualbox yacreader filezilla quiterss winscp wireshark
choco install codeblocks staruml clonespy cygwin pdfsam transmission gpg4win

---

# choco install vcredist-all
choco install vcredist2005 vcredist2008 vcredist2010 vcredist2012 vcredist2013 vcredist140 vcredist2015 vcredist2017  -y
choco install javaruntime jdk8 dotnet directx
choco install sdio # driver manager

choco install azahar dolphin desmume ppsspp
choco install ruby nodejs python netbeans visualstudio2022community sqlitebrowser eclipse

# Other

## texmaker needs miktek installed manually or automatically [texlive]
choco install windirstat anydesk element-desktop teamviewer texmaker git.install
choco install rocketdock cpu-z pcloud dropbox pidgin lmms openshot meld googlejapaneseinput

## Will work, but prefer to install manually

choco install ubooquity jellyfin

## emby? not found on repo.

```

## Powershell Script

```

## VARIABLE_USER

## Extracting User Data
## Don't forget to close the applications before copying to not get "is in use" error.

## Hexchat
Copy-Item -Path "C:\Users\rijndael-box\AppData\Roaming\HexChat" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Roaming" -Recurse -Force
# Local N/A

## qTox
Copy-Item -Path "C:\Users\rijndael-box\AppData\Roaming\tox" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Roaming" -Recurse -Force
# Local N/A

## Veracrypt
Copy-Item -Path "C:\Users\rijndael-box\AppData\Roaming\VeraCrypt" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Roaming" -Recurse -Force
# Local N/A

## Thunderbird
Copy-Item -Path "C:\Users\rijndael-box\AppData\Roaming\Thunderbird" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Roaming" -Recurse -Force
Copy-Item -Path "C:\Users\rijndael-box\AppData\Local\Thunderbird" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Local" -Recurse -Force

## Firefox
Copy-Item -Path "C:\Users\rijndael-box\AppData\Roaming\Mozilla" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Roaming" -Recurse -Force
Copy-Item -Path "C:\Users\rijndael-box\AppData\Local\Mozilla" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Local" -Recurse -Force

## Google Chrome
# Roaming N/A
Copy-Item -Path "C:\Users\rijndael-box\AppData\Local\Google" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Local" -Recurse -Force

## QuiteRSS
Copy-Item -Path "C:\Users\rijndael-box\AppData\Roaming\QuiteRss" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Roaming" -Recurse -Force
Copy-Item -Path "C:\Users\rijndael-box\AppData\Local\QuiteRss" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Local" -Recurse -Force

## IDrive
# Roaming N/A
# Local N/A
Copy-Item -Path "C:\ProgramData\IDrive" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\ProgramData" -Recurse -Force

## Deluge (only if needed)
Copy-Item -Path "C:\Users\rijndael-box\AppData\Roaming\deluge" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Roaming" -Recurse -Force
# Local N/A

## YACReader (only if needed)
# Roaming N/A
Copy-Item -Path "C:\Users\rijndael-box\AppData\Local\YACReader" -Destination "C:\Users\rijndael-box\Downloads\Extracted_Appdata\Local" -Recurse -Force

## Gnu4Win (if needed)
# ... TODO

---

## Applying User Data

...TODO.

```

## Common Steps

1. Login into user account.
2. **Deploy keepass db.**
3. **Deploy cygwin bash library & profile.**
4. **Deploy my icons.**
5. Update system.
6. Install drivers.

---

1. Install chocolatey.
2. Install cygwin.
3. Install winrar.
4. Install keepass.
5. Install veracrypt.
6. Install redist, directx, java, .net, etc.
7. The rest.

## Good Practice

* Separate users into USER and ROOT. **Make sure the Security questions are not as simple as 123, 456... as it can be guessed and this is a huge risk. At least scramble them (mash the keyboard) if you don't care about them.**
* Have root by convention a black/blue solid wallpaper.
* Separate your partitions from the System partition.
* Avoid keeping your data on the machine; preferably store it on external drives or usbs.

## Permissions

Some notes on how Windows permissions work:

First, **ensure you change permissions (usually) from a root/admin account.**

Second, when you right click and Properties, fuck the Edit button at the top/center. Go to **Advanced Settings** to set permissions. That is the main panel for everything.

Third - the OWNER of an entity, pretty much defines the POWER of who can change permissions of said entities.
      - the PERMISSIONS are WHO can access this object/entity. And for the OWNER itself to have access, he needs to be in the permissions.

Now. Another note- IDrive NEEDS access from SYSTEM to work, otherwise it cannot scan the files for backup, even if you run it as a user which has permission.
So, here's how I should set up permissions:

---

OWNER: Root - for all the partitions you want to change.
Permissions: Root, Rijndael-box, SYSTEM. //alternatively, "Root" can be replaced with ADMINISTRATORS. Other tokens that exist for flexibility if needed: Authenticated Users, Users, certain groups. Other owners that exist: TrustedInstaller, certain groups...

Tick the "Replace owners objects" [at the top, in main panel] and "Replace all child object permission entries with inheritable permissions etc". [at the bottom, in main panel]. DO not tick the "Only apply these permissions to objects and/or containers within this container. [when you Add a permission with the Add button].

## Optimizations + Debloating

* Disable Memory Compression
* Disable Disk Drive Protection (Bitlocker)
* Disable Storage Sense

---

* Increase Pagefile size
* Avoid running out of space on the system/os partition
* Partition away from the OS.

---

* Apply a firewall whitelist
* Disable QoS
* Disable Hardware Controls for Edge and Other

---

* Disable Unnecessary Processes
* Disable Unnecessary Services
* Disable Unnecessary Startup Programs

---

* Debloat by uninstalling unnecessary software [use BOTH Add/Remove Software App & Control Panel Uninstall]
  * Onedrive.
  * McAfee
  * McAfee Web Advisor
  * Microsoft Copilot
  * Copilot
  * Xbox
  * Xbox Live
  * Microsoft Teams
  * Microsoft Whiteboard
  * News [if unwanted]
  * Outlook [if unwanted]
  * Microsoft 365 + Office
  * Microsoft Todo
  * Microsoft Clipchamp
  * Smart Connect [lenovo related]

---

* Change Performance Settings
* Disable Windows Features and Services [in Uninstall; like Ms Edge]
* Disable Automatic Updates
* Disable Windows Defender
* Disable Telemetry
* Disable other features [copilot, onedrive, etc [cortana is gone]]
* Disable search indexer
* Disable animations.
* Run explorer.exe with gpu rendering.
* Battery Performance Mode to High if needed.
* Turn off bloated software.
* Group policy editor [if on enterprise; otherwise use registry]
* Control panel
* Registry.
* Power settings.
* Per application optimization (e.g browser, etc) - adblock, etc.
* Process IO/Queue prioritization.
* Appropriate Drivers.


## Quality of Life

* Set file manager to start with devices and drives rather than Home.
* Pin to favourites frequently accessed folder locations you know of.
* Make recycle bin ask for confirmation of deletion.

## UI/UX

* Hide the search box in the taskbar.
* Disable widgets to not show news icon in taskbar.
* Align the start menu to the left.
* Don't set 1920x1080 resolution for desktop. Use 1600x800 and scale it to 100% instead of 125%.

## Privacy

* Folder options - disable the three options for recently used files, and frequently used folders.
* Personalization -> Start -> 4 options to disable here.

## Other

* A microsoft account is needed [make it on the spot if necessary] to make a "main" user.
  * Can create local ones afterwards. Delete the main one after.
  
* Set power settings to never sleep. Good for 24/7 running.

---

## Bit rot, Data Resiliency and RAID

> Bit rot affects data, when still, used, etc, and all data deteriorates, especially media which can produce artifacts, pops, cracks, distortion and so on. In more extreme failures or corruption, the data becomes unusable and must be deleted.

> In some silly (yet smart) cases, you can duplicate some data on the filesystem to create a "soft-level" redundancy. Bit rot will still deteriorate the data but it will prevent situations where, one of the data completely dies, and you still have another copy to work from, even if that copy may be slightly deteriotated.

> ZFS and ReFS are true data integrity solutions that require **manual/automatic** data scrubbing for truly protecting from bit rot.

> By checksumming not just the metadata, but the data itself and having redundant copies internally, corruption from bit rot can be healed from the copy.

> copies=2 is already pretty good, copies=3 is much more powerful.

## Most Setup

* Single device ZFS/ReFS with 3 redundant copies.

## ZFS

* zpool is constructed to have multiple vdevs.
  * **vdevs** (virtual devices) [main concept] are sets of multiple physical disks.
  * special vdevs [used by other vdevs within pool; NOT used by datasets]
    * datasets (special dirs) [partition analogy]
    * zvols for block devices

## ReFS

* Storage Spaces **Pool** [full set of physical devices]
  * Virtual Disk [subset of devices from the full set with config] {aka, the "storage space"}
    * Volumes {the partition itself}
      * Filesystem (ReFs)

## RAID

### Most common/simple types.

* Raid0 -
* Raid1 - 

### For lots of parallelization

...

## Concepts

> Parity - "essentially" pieces of data to reconstruct lost blocks. It's a "cheap" mirroring.
> Mirror - a full redundant copy to reconstruct failures, corruption, lost data from.

