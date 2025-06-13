#Linux #NVIDIA #Brightness #Ubuntu #ElementaryOS
The problem here is the up and down bright buttons don't work and even using `xbacklight` doesn't resolve anything. This problem is caused by the drivers and the grub file and this (in my case) happens using Debian distributions (Ubuntu, Kubuntu, elementaryOS, etc).
Here are the options to resolve this:
## Step 1: Install NVIDIA drivers
Go to `settings > System > Drivers`. And install the driver you want (I've installed the latest, but you can choose anything you want).
![[Drivers.png]]
*(The difference between the options that have open and the other ones that don't have i'ts just the open options are Open Source and the others are Private Source)*

And this is going to installed you NVIDIA X Server Settings to monitorize the GPU of your PC.
## Step 2: Enable backlight and NVIDIA drivers on the GRUB
Open a `terminal` and open the `/etc/default/grub` using `nano` or `vim` (it can be any editor you have in your terminal), you can do it using `sudo vim etc/default/grub` or  `sudo nano etc/default/grub`. 
![[Grub.png]]
Go down to `GRUB_CMDLINE_LINUX_DEFAULT` and add `nvidia-drm.modeset=1 acpi_backlight=native nvidia.NVreg_RegistryDwords=EnableBrightnessControl=1` .
![[Pasted image 20250613154657.png]]
Save and exit (in vim you can use `:wq` and in nano you can use `Crtl+x` , write `y` to save the buffer and `Enter` to save the file).
## Step 3: Update your GRUB
In the terminal write `sudo update-grub` wait until the script done and reboot your PC.