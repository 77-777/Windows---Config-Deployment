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

## Optimizations

* Disable Memory Compression
* Increase Pagefile size
* Avoid running out of space on the system/os partition
* Partition away from the OS.
* Disable QoS
* Disable Unnecessary Processes
* Disable Unnecessary Services
* Debloat by uninstalling unnecessary software
* Change Performance Settings
* Disable Automatic Updates
* Disable Windows Defender
* Apply a firewall whitelist
* Disable Disk Drive Protection (Bitlocker)
* Disable Telemetry
* Disable Storage Sense
* Disable Harware Controls for Edge and Other
* Disable other features [cortana]
* Disable search indexer
* Disable animations.
* Run explorer.exe with gpu rendering.
* Battery Performance Mode to High if needed.
* Turn off bloated software.
