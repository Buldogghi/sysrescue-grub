# Systemrescue for grub

A way to boot into systemrescue directly from grub without an external usb device

<img width="672" height="452" alt="image" src="https://github.com/user-attachments/assets/9c05562c-12a9-4139-92a6-cfef4803b1d4" />

\*The first three entries in the picture are created by default without this script

# Disclaimer

This script doesn't work if you only have windows, you need a bootable Linux partition and obviously Grub as your boot loader.

# What

The systemrescue ISO is a useful arch based 'distro' that shines when it comes to, well, rescuing systems.
This repo's purpose is to have a built-in live ISO with easy access at boot, while not using an external usb drive.

# Why

From my experience using Linux, making mistakes happens like for example by running some scripts from the internet and realizing that your system doesn't boot anymore.
In these cases I like to use the systemrescue ISO from a live USB to chroot into it and hopefully fix the problem, this is where this repo may come in handy!

# How to install

The installation process is relatively straight forward:

- Clone the repo or manually download the '50-systemrescue' file from GitHub.
- Open a terminal in the same folder as the file.
- Make it executable with `chmod +x 50-systemrescue`.
- Make sure that the /etc/grub.d/ directory exists with `sudo mkdir -p /etc/grub.d/`.
- Copy the file to the /etc/grub.d/ directory with `sudo cp 50-systemrescue /etc/grub.d/`.
- Regenerate the grub config with `sudo grub-mkconfig -o /boot/grub/grub.cfg`. (I believe that `sudo update-grub` does the same in Debian based distros)
- Reboot your computer.

Copy and paste command to install:

```
git clone https://github.com/Buldogghi/sysrescue-grub.git
cd sysrescue-grub
chmod +x 50-systemrescue
sudo mkdir -p /etc/grub.d/
sudo cp 50-systemrescue /etc/grub.d/
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

# How to uninstall

The uninstall process is simply:

- Remove the 50-systemrescue file from grub.d with `sudo rm /etc/grub.d/50-systemrescue`.
- Regenerate the grub config by the same way of the install step.

Copy and paste command to uninstall:

```
sudo rm /etc/grub.d/50-systemrescue
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
