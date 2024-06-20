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
