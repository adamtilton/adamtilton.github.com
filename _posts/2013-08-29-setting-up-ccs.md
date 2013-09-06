---
layout: post
category: blog
title: "setting up ccs"
subtitle: "setting up ccs"
thumbnail: 
excerpt: "" 
tags: []
---

[1]: http://processors.wiki.ti.com/index.php/Category:Code_Composer_Studio_v5
[2]: http://www.westernwillow.com/cms/blog/franco/creating-bluetooth-serial-port-ubuntu

# Installing Code Composer Studio Version 5 (CCSv5)

## Steps
1. Visit [here][1] and install code composer studion. A bin file will
   result.
1. Change the the bin file permissions to executable:

  `$ chmod +x ccs_setup_5.4.0.00091.bin`

1. Start the installation process as user, not root:

  `$ ./ccs_setup_5.4.0.00091.bin`

1. Since we installed as user, we must now run these steps to
   install/update the drivers for the JTAG emulators. Follow these
   directions:

    1. Go you your installation directory.
         1. Navigate to the folder: `/ccsv5/install_scripts`.
         1. Run the install_drivers script as root.
              `sudo ./install_drivers.sh`
              This will install/update the necessary files for emulator
              device drivers.

## Resources
1. http://processors.wiki.ti.com/index.php/Code_Composer_Studio_v5_Users_Guide#From_Linux_Command_Line

1. http://processors.wiki.ti.com/index.php/Linux_Host_Support

# Bluetooth Demo
1. Connect the device using Ubuntu Bluetooth functionality
1. Setup a serial port on bluetooth ([reference][2])

  % sudo hcitool scan

  Scanning ...

          00:A0:96:3B:EA:E8       BlueRadios

  $ sudo rfcomm bind /dev/rfcomm0 00:A0:96:3B:EA:E8

  $ ls -l /dev/rfcomm0

  crw-rw---- 1 root dialout 216, 0 Aug 29 16:16 /dev/rfcomm0
1. Install setserial

  $ sudo apt-get install setserial

1. Display detected serial ports

  $ dmesg | grep tty

1. Report I/O port and IRQ port, where # is from above commnad

  $ setserial -g /dev/ttyS#


## References
1. http://linux.die.net/man/1/rfcomm

