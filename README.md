## Installation

1. Disable Secure Boot in bios/uefi
2. connect wifi if on laptop
3. Install arch via archinstall
4. for mirrors choose india and worldwide
5. use btrfs file system
6. additional repos to add: git firefox neofetch nano vlc obsidian qbittorrent unzip xclip reflector rsync
	1. (DONT install code, rather install the pre-built version. the community addition sucks)
7. Don't enable testing or multilib
8. Use pipewire for audio

My current setup working perfectly:
https://www.youtube.com/watch?v=WuZ2T6D_9yI
https://github.com/prasanthrangan/hyprdots?tab=readme-ov-file

---
### Additional Setups

##### Mirrors (For Download speed) 

```bash
# Backup old mirrorlist
sudo cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlistBackup

# Install Reflector if not done during install
sudo pacman -S reflector

# Run to get optimal mirrors
sudo reflector --verbose --sort rate -l 350 --save /etc/pacman.d/mirrorlist
```

##### Make another command with the same name
(i.e clear -> cls)
```bash
cd /user/bin
sudo cp <commandName> <newCommand name>
```

##### Install Node.js, npm and pnpm
```bash
sudo pacman -S nodejs npm

sudo npm install -g pnpm
```

##### Install Vscode
```bash
yay -S visual-studio-code-bin
```

##### Configuring Multiple Monitors and adjust display

**Figure out which monitor is which by running the command below**
```
hyprctl monitors all
```

**Add Monitors in the hyprland.conf**
```bash 
cd .config/hypr
```

Path: /home/elusive/.config/hypr/hyprland.conf

```config
monitor=eDP-1,1920x1080@60,0x0,1.0
monitor=HDMI-A-1,1920x1080@60,-1920x0,1.0 # Monitor to the left
```

> turn the -1920 into 1920 to make this a monitor on the right

##### Adjust Focus in Hyprland
in input object of hyprland.conf
```
follow_mouse = 2 
```

##### **Install Fonts**
[Download](https://www.jetbrains.com/lp/mono/) JetBrains Mono and follow these [instructions](https://www.jetbrains.com/lp/mono/#how-to-install).

##### **Keybind for multiple firefox profiles:**
Add the following keybinds to the keybinds.conf in .config/hypr/keybinds.conf
```
bind = $mainMod, F1, exec, $browser -P "work" # launch web browser
bind = $mainMod, F2, exec, $browser -P "prod" # launch web browser
bind = $mainMod, F3, exec, $browser -P "elusive" # launch web browser
```


##### **Adjust Fullscreen setting so it keeps the bar**
```
# In keybinds.conf inside .config/hypr
bind = Alt, Return, fullscreen,1 # toggle the window between focus and fullscreen
```

##### **Setup pCloud for drive**
```
yay -S pcloud-drive
```


##### **Mount Another Drive Automatically**
1 - Run the command below to list all of the blocks of storage along with their file types (-f)
```
lsblk -f
```

2 - Create  a mount point
```
sudo mkdir /mnt/data
```

3 - Update the fstab in etc
```
sudo nano /etc/fstab
```

4 - Add the following line at the bottom of the fstab making sure to update the UUID and file_sys from the step 1
```
UUID=your_UUID /mnt/data file_sys defaults 0 2
```

---
#### Extra Stuff
##### Format a USB Drive
```
# identify
lsblk 

# lets say after identification its sdb and partition 1
sudo umout /dev/sdb1
sudo fdisk /dev/sdb
type d to delete any existing partitions.

// Then type n to create a new partition. Choose partition number 1 and accept the defaults for the first two prompts.

// Finally, type w to write the changes to the disk.
```


sudo mkfs.ntfs --label <USBNAME> /dev/sdb1


//Update opacity in windowrules.conf



// Download Yay (package manager) avoids having to clone each repo then makepkg

sudo pacman -Syu
sudo pacman -S git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -sri

// install docker
sudo pacman -S gnome-terminal
https://docs.docker.com/desktop/install/archlinux/
