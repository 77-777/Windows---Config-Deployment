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

choco install veracrypt keepass deluge firefox winrar
choco install googlechrome hexchat vlc steam libreoffice-fresh
choco install notepadplusplus thunderbird handbrake cherrytree gimp
choco install calibre adobereader 7zip idrive freedownloadmanager

choco install imagemagick caesium.install freemind qtox atom
choco install anki blender inkscape krita audacity obs-studio
choco install virtualbox yacreader filezilla quiterss winscp wireshark
choco install codeblocks staruml clonespy cygwin pdfsam transmission

# choco install vcredist-all
choco install vcredist2005 vcredist2008 vcredist2010 vcredist2012 vcredist2013 vcredist140 vcredist2015 vcredist2017  -y
choco install javaruntime jdk8 dotnet directx
choco install sdio # driver manager

choco install azahar dolphin desmume ppsspp
choco install ruby nodejs python netbeans visualstudio2022community sqlitebrowser eclipse

# Other

choco install windirstat anydesk element-desktop teamviewer texmaker git.install rocketdock cpu-z pcloud dropbox pidgin lmms openshot meld googlejapaneseinput

## Will work, but prefer to install manually

choco install ubooquity jellyfin

## emby? not found on repo.

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
