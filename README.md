# LINUX_RTOS 
Debian 10 Buster - 4.19.0-11-rt-amd64 kernel

![alt text](https://github.com/grotius-cnc/LINUX_RTOS/blob/main/screenshot_800.png)

- Libreoffice
- Geany
- Glade linuxcnc widgets
- QT5 designer
- HG Ehtercat
- Linuxcnc reprository

Iso download 1.7 gb :
https://github.com/grotius-cnc/LINUX_RTOS/releases/tag/1.0.0

During installtion, keep root password entry empty !

After installation, select the Ethercat_installer desktop launcher. This will auto install the ethercat bus.
Done.

* User info :

The configuration to check the working ethercat bus is done with the Beckhoff EK1100 module. You can connect this device before installing the iso cd.
During installation of the iso cd, you could use usb tethering for internet connection to setup your nearest download mirror while the ethercat bus uses
your cat4 connection.

After iso installation, select the Ethercat_installer desktop launcher. This will auto install the ethercat bus. Bus lights will be flickering fast during
ethercat bus installation. If not, restart pc after installation. 

The ethercat installation could be done over again without concequences. 
If you have custom lcec drivers, save them outside the /usr/share/ethercat directory.

After the ethercat installation, start the linuxcnc desktop launcher, the lcec will show up in Linuxcnc "show hal configuration". 
Add your I/O modules to your needs in the linuxcnc_axis desktop map ethercat-conf.xml.
Connect your I/O modules to linuxcnc in the hal file, in this axis-qtvcp example it uses the qtvcp_postgui.hal file to connect the ethercat I/O

Ethercat source : $ /usr/share/ethercat


* Live build info :

Rebrand your iso to your wishes with a pre-configured live-build in :  $ /usr/share/ethercat/setup_iso.sh

For example if you want to update or downgrade the kernel, change the kernel image and header description in setup_iso.sh at :
- linux-image-4.19.0-11-rt 
- linux-headers-4.19.0-11-rt 
Available kernel packages can be found : https://packages.debian.org/buster/kernel/

Tip : Don't copy files to usb unless they are in archive (zip) format. 
Otherwise during copy it could change file permission's. The setup_iso.sh must be set as read/write.

More recource files for building live-build's : 
- https://sourceforge.net/projects/eznixos/   
- https://github.com/LinuxCNC/buster-live-build

In short, the live build commands are :

 - #!/bin/bash
 - apt-get install live-build
 - lb clean
 - lb config
 - add packages and config here, see setup_iso.sh
 - lb build
