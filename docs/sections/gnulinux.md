## GNU/Linux general and agnostic views.

### Some thoughts about distributions:

<div style="text-align: justify;">
In my view, Linux distributions are essentially collections of software projects available across the web, seamlessly integrated to achieve specific goals. These goals can range from assembling suites of tools for particular tasks—such as networking, multimedia, overall user experience, academic research, system administration, enterprise solutions, mission-critical computing, or IT enthusiast garage projects—to virtually any purpose one can imagine.

Creating a distribution requires significant time, effort, and dedication. The teams or individuals behind each project deserve respect for their contributions. From my perspective, there’s no such thing as a "bad" Linux distro; at most, a distro might not align with my specific needs. In such cases, I simply look for another project that better fits my requirements and viewpoints.

With this mindset, I’ve decided to streamline my workflow. Previously, I maintained numerous random text files with notes on how to perform various tasks while tweaking the Linux distributions I use. To achieve better mental peace and organization, I embarked on a documentation project. This project consolidates the information I frequently refer to when setting up different environments, which is essentially what I do every day.
</div>


### Linux distros I usually work with:

#### OpenSuSE Tumbleweed.

##### Basic Package Management 

**Refresh Repositories** 

```bash
sudo zypper refresh
```

Refreshes the package database from configured repositories.
**Update All Packages** 

```bash
sudo zypper update
```

Updates all installed packages to their latest versions.
**Install a Package** 

```bash
sudo zypper install <package_name>
```

Installs the specified package.
**Remove a Package** 

```bash
sudo zypper remove <package_name>
```

Removes the specified package.
**Search for a Package** 

```bash
zypper search <package_name>
```

Searches for a package by name.
**Get Package Information** 

```bash
zypper info <package_name>
```

Displays detailed information about a specified package.
**List Installed Packages** 

```bash
zypper list-updates
```

Lists all installed packages and their current versions.
**Repository Management** **Add a Repository** 

```bash
sudo zypper addrepo <repo_URL> <repo_alias>
```

Adds a new repository with the specified URL and alias.
**Remove a Repository** 

```bash
sudo zypper removerepo <repo_alias>
```

Removes the repository with the specified alias.
**List All Repositories** 

```bash
zypper repos
```

Lists all configured repositories.
**Enable a Repository** 

```bash
sudo zypper modifyrepo --enable <repo_alias>
```

Enables the specified repository.
**Disable a Repository** 

```bash
sudo zypper modifyrepo --disable <repo_alias>
```

Disables the specified repository.
**Advanced Package Management** **Update a Specific Package** 

```bash
sudo zypper update <package_name>
```

Updates the specified package to its latest version.
**Install a Package from a Specific Repository** 

```bash
sudo zypper install --from <repo_alias> <package_name>
```

Installs the specified package from the given repository.
**Clean the Cache** 

```bash
sudo zypper clean
```

Cleans the local cache of repository metadata.
**View Patch Information** 

```bash
zypper list-patches
```

Lists available patches for the system.
**Install Specific Version of a Package** 

```bash
sudo zypper install <package_name>=<version>
```

Installs a specific version of the specified package.
**Lock/Unlock Packages** **Lock a Package** 

```bash
sudo zypper addlock <package_name>
```

Prevents the specified package from being updated.
**Unlock a Package** 

```bash
sudo zypper removelock <package_name>
```

Removes the lock on the specified package, allowing it to be updated.
**Miscellaneous Commands** **Show Package Dependencies** 

```bash
zypper info --requires <package_name>
```

Shows the dependencies of the specified package.
**Check for Package Conflicts** 

```bash
zypper verify
```

Things to do after installing OpenSuSE
** Installing some repos: **

```bash

zypper ar -cfp 90 'https://ftp.gwdg.de/pub/linux/misc/packman/suse/openSUSE_Tumbleweed/Essentials/' packman-essentials
zypper ar -cfp 90 'https://ftp.gwdg.de/pub/linux/misc/packman/suse/openSUSE_Tumbleweed/Multimedia/' packman-multimedia
zypper addrepo https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo
```
** Some common used multimedia packages **

```bash

zypper install --allow-vendor-change audacious aria2 avidemux3-qt5 btop catfish chromium clementine cockpit cockpit-bridge cockpit-machines cockpit-networkmanager cockpit-packagekit cockpit-selinux cockpit-storaged cockpit-system cockpit-ws dc3dd ecryptfs-utils filezilla gimp git-core glances gmplayer gparted gstreamer-plugins-bad gstreamer-plugins-libav gstreamer-plugins-ugly gstreamer-plugins-ugly-orig-addon guake guake handbrake-gtk hplip hplip-scan-utils htop inkscape inkscape-extensions-extra inkscape-extensions-gimp k3b kdenlive keepassxc krusader lame lsof mc mplayer neofetch neovim nmap obs-studio openscad pavucontrol-qt pcmanfm qalculate-qt qbittorrent qdirstat QMPlay2 qmmp retroarch smplayer soundconverter soundkonverter spacefm telegram-desktop terminator testdisk thunderbird uget virtualbox vlc-codecs wine wireshark-ui-qt
```


#### Arco Linux

#### Debian

##### A fairly updated Debian/GNU Linux sources.list

##### sources.list

```bash
# deb cdrom:[Debian GNU/Linux 11.3.0 _Bullseye_ - Unofficial amd64 NETINST with firmware 20220326-11:22]/ bullseye contrib main non-free

#deb cdrom:[Debian GNU/Linux 11.3.0 _Bullseye_ - Unofficial amd64 NETINST with firmware 20220326-11:22]/ bullseye contrib main non-free

deb http://deb.debian.org/debian/ bookworm main non-free non-free-firmware contrib
deb-src http://deb.debian.org/debian/ bookworm main non-free contrib non-free-firmware

deb http://security.debian.org/debian-security bookworm-security main contrib non-free
deb-src http://security.debian.org/debian-security bookworm-security main contrib non-free

# bullseye-updates, to get updates before a point release is made;
# see https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_updates_and_backports
deb http://deb.debian.org/debian/ bookworm-updates main contrib non-free
deb-src http://deb.debian.org/debian/ bookworm-updates main contrib non-free

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.

deb https://www.deb-multimedia.org bookworm main non-free

# deb http://deb.debian.org/debian/ trixie main non-free non-free-firmware contrib
# deb-src http://deb.debian.org/debian/ trixie main non-free contrib non-free-firmware

```

