# LOG WEEK 9


Here are the steps when I tried to compile my own version of linux kernel.
I used VirtualBox and the OVA given at the start of the course.

**Setting up PuTTY**
Before starting up the OVA, first check the network settings. Then drop down the advanced option, and click port forwarding. In the window, note the Host IP and Host Port. After that, open your PuTTY, then fill the Hostname part with the Host IP or "localhost" and fill the Port with Host Port. Wait until the VM is turned on (the screen asks for user name), then go back to PuTTy and click Open.

**Setting up core and RAM**
Go to system settings in your virtualbox. To change the amount of RAM used, you can change it in the motherboard tab, and for your CPU Core, change it in the processor tab. The more you use the faster the compiling process, but your computer will also use most of its resources on compiling. Make sure you have enough memory space as well.

After you have set up the virtualbox, turn it on and wait until it is finished loading. When the vbox screen asks you for your username, click Open in PuTTY, then enter your username and password.

**Getting the Linux kernel**
After logging in, first of all make sure you are in the folder you want to do your work. In this log the kernel version used is 4.15.1. Then, download the linux kernel using wget (For me I used wget http://kambing.ui.ac.id/linux/v4.x/linux-4.15.1.tar.xz), then extract the tar by running tar -xvJf linux-4.15.1.tar.xz. After that, you can open the extracted folder to check the insides.

**Getting the config file**
It is recommended to use currently working config, because we know that it is working. So, go to the /boot folder, and take note of the versions available by running ls. Pick the version you want (in case there are more than one version), then note the config file down. Go back to the linux kernel folder you've downloaded, then copy-paste the config file by using cp (Ex: cp /boot/(your chosen config) .config)

*NOTE: from here on out, it is highly recommended to change to superuser mode by doing "sudo su", as most of the commands will need superuser privilege.*

**Downloading the dependencies**
Get the dependencies needed to compile your kernel, here is the dependencies that I use:
- sudo apt-get install build-essential linux-source bc kmod cpio flex libncurses5-dev libelf-dev
- sudo apt-get install kernel-package
- sudo apt-get install libncurses5-dev
- sudo apt-get install flex bison
- sudo apt-get install libssl-dev
- sudo apt-get install build-essential

**Make menuconfig**
Run "make menuconfig", there should be a GUI loaded to your terminal. Go to the Load option, the GUI will ask you for the config file (default is .config). Because you've copied the config file earlier, you can just press enter and exit.

**Compiling kernel**
Before compiling, export your concurrency level by running this: "export CONCURRENCY_LmakEVEL=(your allocated core - 1)". For example, you set up your Vbox so that it uses 8 core, so you would run export CONCURRENCY_LmakEVEL=8.
After that, clean the folder by using "sudo make-kpkg clean", and compile by running this:
***sudo make-kpkg -j (allocated core) --initrd --append-to-version=<version_name> kernel_image kernel_headers***
For your version name, you can fill it with anything you want (for example, your identity).
After running the command, leave your computer for a while as it will start compiling the kernel. When it is done, go back one folder to your work folder that contains the linux kernel folder, then run ls. There should be a new kernel_image and kernel_headers file.

**Installing kernel**
Simply run the following commands:
- sudo dpkg -i linux-headers-4.15.1<version_name>_4.15.1<version_name>-10.00.Custom_amd64.deb
- sudo dpkg -i linux-image-4.15.1<version_name>_4.15.1<version_name>-10.00.Custom_amd64.deb

**Install modules**
Go to your kernel folder, then run "sudo make modules_install".

**Updating initramfs**
Go to the /boot/ folder, run "sudo update-initramfs -c -k vmlinuz-4.15.1<version_name>".

**Updating grub, Modifying grub**
Simply run "sudo update-grub".
If you want to modify the grub file, run "sudo vi /etc/default/grub", and it will take you to vim text editor. Go to insert mode by pressing I, and edit the file as you want. In my case, the edits I've made are:
#GRUB_TIMEOUT_STYLE=hidden

GRUB_TIMEOUT=10
After you're done, press ESC to go back, type and enter :w to save and :q to quit the editor.
Don't forget to update the grub again.

**Making sure your version is installed**
Restart your machine, and in your OVA, there should be a new menu. Go to the advanced settings one, your version should be listed in there. Pick that one and enter, and after you've logged in (either from PuTTY or from the OVA).
Run "uname -a", and your version should be printed to the terminal.

**Problems I've encountered**
The first problem I've had was when I compiled for the first time, I realized there was some modules missing, so I installed more dependencies. After that, I compiled without being the superuser, so there were some permissions denied. I managed to fix it by simply adding sudo in the front of the command.
