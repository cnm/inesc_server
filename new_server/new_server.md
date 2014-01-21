**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Hardware](#hardware)
- [IPMI Remote management](#ipmi-remote-management)
- [RAID](#raid)
- [Installation](#installation)
    - [install bcache](#install-bcache)
    - [LVM](#lvm)
- [Small tweaks](#small-tweaks)
- [Packages to be installed](#packages-to-be-installed)
- [TODO](#todo)

Hardware
--------

* CPU: 2 x Intel Xeon E5-2640V2, LGA 2011, 2.0GHz, 8C/16T
* RAM: 8 x DDR3 REG16G-1600DDR3, 16GB, DDR3-1600, Registered ECC, memory
* Raid Controller: Backup for LSI SAS2208 + Bracket
* Server: Supermicro SuperServer 6027R-72RF
* Network cards: 2 x Intel Corporation I350 Gigabit Network Connection (rev 01)
  - eth0 (left): 00:25:90:e1:45:62 --> 172.20.41.138
  - eth1 (right): 00:25:90:e1:45:63
* IPMI
  - Mac address: 00-25-90-ce-d6-f6 --> 172.20.41.197
* Disks:
   - Disk IDs were discovered with the following command:
     - 'find /dev/disk/by-id/ -iname 'scsi-*' | grep -v -- -part | while read disk ; do echo $(readlink $disk | sed -e s:../../:: ) $(basename $disk); done'

   - 2x SAMSUNG SSD 840 PRO 256GB SATA III
   - 4x WESTERN DIGITAL 3TB SATA III 64MB RED


* lspci command:

        00:00.0 Host bridge: Intel Corporation Ivytown DMI2 (rev 04)
        00:01.0 PCI bridge: Intel Corporation Device 0e02 (rev 04)
        00:02.0 PCI bridge: Intel Corporation Ivytown PCI Express Root Port 2a (rev 04)
        00:02.2 PCI bridge: Intel Corporation Ivytown PCI Express Root Port 2c (rev 04)
        00:03.0 PCI bridge: Intel Corporation Ivytown PCI Express Root Port 3a (rev 04)
        00:03.2 PCI bridge: Intel Corporation Ivytown PCI Express Root Port 3c (rev 04)
        00:04.0 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 0 (rev 04)
        00:04.1 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 1 (rev 04)
        00:04.2 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 2 (rev 04)
        00:04.3 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 3 (rev 04)
        00:04.4 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 4 (rev 04)
        00:04.5 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 5 (rev 04)
        00:04.6 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 6 (rev 04)
        00:04.7 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 7 (rev 04)
        00:05.0 System peripheral: Intel Corporation Ivytown VTd/Memory Map/Misc (rev 04)
        00:05.2 System peripheral: Intel Corporation Ivytown IIO RAS (rev 04)
        00:05.4 PIC: Intel Corporation Ivytown IOAPIC (rev 04)
        00:11.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port (rev 06)
        00:16.0 Communication controller: Intel Corporation C600/X79 series chipset MEI Controller #1 (rev 05)
        00:16.1 Communication controller: Intel Corporation C600/X79 series chipset MEI Controller #2 (rev 05)
        00:1a.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 (rev 06)
        00:1d.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 (rev 06)
        00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
        00:1f.0 ISA bridge: Intel Corporation C600/X79 series chipset LPC Controller (rev 06)
        00:1f.2 SATA controller: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller (rev 06)
        00:1f.3 SMBus: Intel Corporation C600/X79 series chipset SMBus Host Controller (rev 06)
        01:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 2208 [Thunderbolt] (rev 05)
        05:00.0 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
        05:00.1 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
        07:00.0 Serial Attached SCSI controller: Intel Corporation C602 chipset 4-Port SATA Storage Control Unit (rev 06)
        08:03.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 (rev 0a)
        7f:08.0 System peripheral: Intel Corporation Ivytown QPI Link 0 (rev 04)
        7f:09.0 System peripheral: Intel Corporation Ivytown QPI Link 1 (rev 04)
        7f:0a.0 System peripheral: Intel Corporation Ivytown Power Control Unit 0 (rev 04)
        7f:0a.1 System peripheral: Intel Corporation Ivytown Power Control Unit 1 (rev 04)
        7f:0a.2 System peripheral: Intel Corporation Ivytown Power Control Unit 2 (rev 04)
        7f:0a.3 System peripheral: Intel Corporation Ivytown Power Control Unit 3 (rev 04)
        7f:0b.0 System peripheral: Intel Corporation Ivytown Semaphore and Scratchpad Configuration Registers (rev 04)
        7f:0b.3 System peripheral: Intel Corporation Ivytown Semaphore and Scratchpad Configuration Registers (rev 04)
        7f:0c.0 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0c.1 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0c.2 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0c.3 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0d.0 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0d.1 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0d.2 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0d.3 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        7f:0e.0 System peripheral: Intel Corporation Ivytown Home Agent 0 (rev 04)
        7f:0e.1 Performance counters: Intel Corporation Ivytown Home Agent 0 (rev 04)
        7f:0f.0 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Target Address/Thermal Registers (rev 04)
        7f:0f.1 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 RAS Registers (rev 04)
        7f:0f.2 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        7f:0f.3 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        7f:0f.4 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        7f:0f.5 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        7f:10.0 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 0 (rev 04)
        7f:10.1 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 1 (rev 04)
        7f:10.2 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 ERROR Registers 0 (rev 04)
        7f:10.3 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 ERROR Registers 1 (rev 04)
        7f:10.4 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 2 (rev 04)
        7f:10.5 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 3 (rev 04)
        7f:10.6 System peripheral: Intel Corporation Device 0eb6 (rev 04)
        7f:10.7 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 ERROR Registers 2 (rev 04)
        7f:13.0 System peripheral: Intel Corporation Ivytown R2PCIe (rev 04)
        7f:13.1 Performance counters: Intel Corporation Ivytown PCI Express Ring Performance Monitoring (rev 04)
        7f:13.4 System peripheral: Intel Corporation Ivytown QPI Ring Registers (rev 04)
        7f:13.5 Performance counters: Intel Corporation Ivytown QPI Ring Performance Ring Monitoring (rev 04)
        7f:16.0 System peripheral: Intel Corporation Ivytown System Address Decoder (rev 04)
        7f:16.1 System peripheral: Intel Corporation Ivytown Broadcast Registers (rev 04)
        7f:16.2 System peripheral: Intel Corporation Ivytown Broadcast Registers (rev 04)
        80:01.0 PCI bridge: Intel Corporation Device 0e02 (rev 04)
        80:02.0 PCI bridge: Intel Corporation Ivytown PCI Express Root Port 2a (rev 04)
        80:02.2 PCI bridge: Intel Corporation Ivytown PCI Express Root Port 2c (rev 04)
        80:03.0 PCI bridge: Intel Corporation Ivytown PCI Express Root Port 3a (rev 04)
        80:04.0 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 0 (rev 04)
        80:04.1 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 1 (rev 04)
        80:04.2 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 2 (rev 04)
        80:04.3 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 3 (rev 04)
        80:04.4 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 4 (rev 04)
        80:04.5 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 5 (rev 04)
        80:04.6 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 6 (rev 04)
        80:04.7 System peripheral: Intel Corporation Ivytown Crystal Beach DMA Channel 7 (rev 04)
        80:05.0 System peripheral: Intel Corporation Ivytown VTd/Memory Map/Misc (rev 04)
        80:05.2 System peripheral: Intel Corporation Ivytown IIO RAS (rev 04)
        80:05.4 PIC: Intel Corporation Ivytown IOAPIC (rev 04)
        ff:08.0 System peripheral: Intel Corporation Ivytown QPI Link 0 (rev 04)
        ff:09.0 System peripheral: Intel Corporation Ivytown QPI Link 1 (rev 04)
        ff:0a.0 System peripheral: Intel Corporation Ivytown Power Control Unit 0 (rev 04)
        ff:0a.1 System peripheral: Intel Corporation Ivytown Power Control Unit 1 (rev 04)
        ff:0a.2 System peripheral: Intel Corporation Ivytown Power Control Unit 2 (rev 04)
        ff:0a.3 System peripheral: Intel Corporation Ivytown Power Control Unit 3 (rev 04)
        ff:0b.0 System peripheral: Intel Corporation Ivytown Semaphore and Scratchpad Configuration Registers (rev 04)
        ff:0b.3 System peripheral: Intel Corporation Ivytown Semaphore and Scratchpad Configuration Registers (rev 04)
        ff:0c.0 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0c.1 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0c.2 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0c.3 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0d.0 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0d.1 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0d.2 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0d.3 System peripheral: Intel Corporation Ivytown Unicast Registers (rev 04)
        ff:0e.0 System peripheral: Intel Corporation Ivytown Home Agent 0 (rev 04)
        ff:0e.1 Performance counters: Intel Corporation Ivytown Home Agent 0 (rev 04)
        ff:0f.0 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Target Address/Thermal Registers (rev 04)
        ff:0f.1 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 RAS Registers (rev 04)
        ff:0f.2 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        ff:0f.3 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        ff:0f.4 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        ff:0f.5 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
        ff:10.0 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 0 (rev 04)
        ff:10.1 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 1 (rev 04)
        ff:10.2 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 ERROR Registers 0 (rev 04)
        ff:10.3 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 ERROR Registers 1 (rev 04)
        ff:10.4 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 2 (rev 04)
        ff:10.5 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 Thermal Control 3 (rev 04)
        ff:10.6 System peripheral: Intel Corporation Device 0eb6 (rev 04)
        ff:10.7 System peripheral: Intel Corporation Ivytown Integrated Memory Controller 1 Channel 0-3 ERROR Registers 2 (rev 04)
        ff:13.0 System peripheral: Intel Corporation Ivytown R2PCIe (rev 04)
        ff:13.1 Performance counters: Intel Corporation Ivytown PCI Express Ring Performance Monitoring (rev 04)
        ff:13.4 System peripheral: Intel Corporation Ivytown QPI Ring Registers (rev 04)
        ff:13.5 Performance counters: Intel Corporation Ivytown QPI Ring Performance Ring Monitoring (rev 04)
        ff:16.0 System peripheral: Intel Corporation Ivytown System Address Decoder (rev 04)
        ff:16.1 System peripheral: Intel Corporation Ivytown Broadcast Registers (rev 04)
        ff:16.2 System peripheral: Intel Corporation Ivytown Broadcast Registers (rev 04)


IPMI Remote management
----------------------

    * Point the browser to the IPMI interface IP

    * Use IPMIView
        - ftp://ftp.supermicro.com/utility/IPMIView/Linux/

    * Disable IPMI access via normal interface
        * Using the web browser IPMI page
            - In configuration -> network
            - Lan Interface -> Dedicate
            - Save


RAID
----

By hardware:

Manual for the software available [here](http://www.lsi.com/downloads/Public/MegaRAID%20Common%20Files/51530-00_Rev_L.zip)

    Drive Groups
        - Virtual Drive 0 - RAID 1 - 237.486 GB
            - Slot:3, SATA, SDD
            - Slot:7, SATA, SDD

        - Virtual Drive 1 - RAID 5 - 8.185TB
            - Slot:0, SATA, HDD
            - Slot:1, SATA, HDD
            - Slot:4, SATA, HDD
            - Slot:5, SATA, HDD

Partion by software:

        - Virtual Drive 0
            Partitions
                - 16G - Swap
                - 40G - /
                - Rest (184) - Reserved for bcache

        - Virtual Drive 1
            Partition
               - 8.165TB all used with bcache
                   - lvm on the bcache partition
                        - /home (5TB)
                        - /tmp  (300GB)
                        - /var  (5GB)
                        - free for future use

Installation
------------

Debian installation steps:

    * NetInstall Stable x64
    * Language: English
    * Country: Other, Europe, Portugal
    * Locale: United States
    * Keymap: Portuguese
    * Primary Interface
    * Hostname: citysdk
    * Domain Name: tecnico.ulisboa.pt
    * Archive Mirror: Portugal, mirrors.nfsi.pt
    * Proxy: (blank)
    * Root Password:
    * Full Name New User:
    * username/pass:
    * Time location: Lisbon

    * Disk partition
        - Manual
            - SDB - 255.0 GB
                - Create new partition table <Yes>
                - Select created free-space, create new partition
                    - Partition size: 16GB
                    - Location beginning
                    - Name: swap
                    - Use as -> swap area
                    - Done setting partition
                - Select the 239 free-space, create new partition
                    - Partition size: 40GB
                    - Location beginning
                    - Name: OS
                    - Use as -> Ext4 journal system
                    - Mount point: /
                    - Mount option: default
                    - Bootable flag: On
                    - Done setting partition
                - Select the 199 free-space, create new partition
                    - Partition size: 200MB
                    - Location beginning
                    - Name: EFI_BOOT
                    - Use as -> EFI boot partition
                    - Done setting partition
                - Select the 198.8 free-space, create new partition
                    - Partition size: 100%
                    - Location beginning
                    - Name: SSD_CACHE
                    - Use as -> Do not use
                    - Done setting partition
            - SDA - 255.0 GB
                - Create new partition table <Yes>
                - Select the 9TB free-space, create new partition
                    - Partition size: 100%
                    - Location beginning
                    - Name: LARGE_VD
                    - Use as -> Do not use
                    - Done setting partition
    * Select repo
        portugal -> mirrors.nfsi.pt

    * Reboot


install bcache
==============

    * Add ist ciist repos
        - Add to /etc/apt/sources.list

    deb http://debian.ist.utl.pt/ciist wheezy internal other non-chef
    deb http://debian.ist.utl.pt/ciist squeeze internal other non-chef

    * Add ciist key

    wget -qO - "http://estocolmo.ist.utl.pt/ciist.key" | apt-key add -

    * Install dsi kernels

        - aptitude update && aptitude install linux-image-3.13.0-rc2-dsi

    * Install bcache userspace utils

        - aptitude install bcache-tools

    * Install parted tools

        - aptitude install parted

    * confirm the partitions (from now assume sda4 == SSD_CACHE && sdb1 == LARGE_VD)

        - parted list

    * Create backing device (the mechanical disks)

        - make-bcache -b 1024kb -B /dev/sdb1

    * Create cache device (the ssd disks)

        - make-bcache -b 1024kb -C /dev/sda4

    * Register the cache device against your backing device. We need to find the UUID of your cache device and then add it to the bcache device initially. Udev rules will take care of this on reboot and will only need to be done once.

        - cd /sys/fs/bcache
        - ls
        - echo *-*-*-*-* > /sys/block/bcache0/bcache/attach

    *  Change your cache mode (if you want to cache writes as well as reads):

        - echo writeback > /sys/block/bcache0/bcache/cache_mode

    * Reboot (check if really necessary)

    * We now have a /dev/bcache0

    * Create a new disk label (i wanted to use gpt, but lvm does not work)

        - parted /dev/bcache0 mklabel msdos

Testing bcache speed
____________________

* Install fio
        aptitude install fio

* fio configuration file (tests.fio)

        [global]
        bs=4k
        ioengine=libaio
        iodepth=32
        size=16g
        direct=1
        runtime=60
        directory=/home/jtrindade/tests
        filename=fio_test.file

        [seq-read]
        rw=read
        stonewall

        [rand-read]
        rw=randread
        stonewall

        [seq-write]
        rw=write
        stonewall

        [rand-write]
        rw=randwrite
        stonewall

* Run fio

    fio test.fio > results.txt

* Result file is here:

    https://github.com/cnm/inesc_server/blob/master/new_server/bcache_results.md

LVM
===

    * Install lvm2

        - aptitude install lvm2

    * Add bcache id type to lvm

        - In line 100 of /etc/lvm/lvm.conf add:

            types = [ "bcache", 16 ]

    * Create physical volume (pv)

        - pvcreate /dev/bcache0

    * Check with pvdisplay

    * Create volume group (vg)

        - vgcreate vg_data /dev/bcache0

    * Check with vgdisplay and vgscan

    * Create the logical volumes (lv)

        - lvcreate --name tmp --size 300G vg_data
        - lvcreate --name var --size 5G vg_data
        - lvcreate --name home --size 5TB vg_data

    * Check with lvdisplay and lvscan

    * Create the filesystems

        - mkfs.ext4 /dev/vg_data/tmp
        - mkfs.ext4 /dev/vg_data/var
        - mkfs.ext4 /dev/vg_data/home

    * Copy all the content to the new directories (tmp is not necessary)

        - mkdir /tmp/var && mount /dev/vg_data/var /tmp/var && cp -av /var/* /tmp/var; umount /tmp/var
        - mkdir /tmp/home && mount /dev/vg_data/home /tmp/home && cp -av /home/* /tmp/home; umount /tmp/home
        - chmod 1777 /tmp   # TODO (confirm if this is the best option)

    * Change the fstab to include

        # lvm partitions
        /dev/vg_data/var  /var auto    defaults  0       0
        /dev/vg_data/tmp  /tmp auto    defaults  0       0
        /dev/vg_data/home /home auto   defaults  0       0

Acl
---

    * Install acl
        apt-get install acl

User quota
----------

    * Install quota
        apt-get install quota

    * Activate user quota
        Edit /etc/fstab
            /dev/vg_data/home /home auto   usrquota,defaults  0       0

    * Set quota for new users
        In /etc/adduser.conf
            set QUOTAUSER="jtrindade" # TODO Maybe a normal user would be best

    * Set the quota for default user (50 GB soft, 100 GB hard)
        setquota -u jtrindade 50000000 100000000 0 0 /dev/vg_data/home

Small tweaks
------------

Ssh
###

    * Disable root login
        Edit /etc/ssh/sshd_config
            PermitRootLogin no

Sudo
####

    * Add admins to sudoers group
        adduser foo sudo

Cacti
-----

    * Install cacti
        apt-get install cacti

    * This will install mysql, just enter the root password for mysql

    * Enter the root password for mysql

    * Enter the password for cacti user in mysql

    * Open browser at http://localhost/cacti

    * Next -> new_install -> Check if found everything -> Finish

    * User: admin pass:admin

    * Import template here **TODO**

    * Install snmp ???? **TODO**

    * Put cacti on https (only) **TODO**

Logcheck
--------

    * Install logcheck
        apt-get install logcheck

    * Specify admin email address and the report level in the /etc/logcheck/logcheck.conf

        # Controls the level of filtering:
        # Can be Set to "workstation", "server" or "paranoid" for different
        # levels of filtering. Defaults to server if not set.

                 REPORTLEVEL="server"

        # Controls the address mail goes to:
        # *NOTE* the script does not set a default value for this variable!
        # Should be set to an offsite "emailaddress@some.domain.tld"

                SENDMAILTO="trindade.joao@gmail.com"

Schroot (very usefull for Trindade simulations)
-----------------------------------------------

    * Install schroot
        apt-get install schroot

    * Create directory /etc/schroot/qualnet

    * Create file /etc/schroot/chroot.d/hardy_amd64_jtrindade
         [hardy_amd64]
         type=directory
         #type=plain
         description=Ubuntu 8.04 Hardy for amd64
         directory=/home/cnm/jtrindade/chroot/hardy_amd64
         #personality=linux32
         root-users=jtrindade
         #run-setup-scripts=true
         #run-exec-scripts=true
         #type=directory
         users=jtrindade
         aliases=qualnet
         script-config=qualnet/config

    * Create file /etc/schroot/qualnet/config

        # Settings for "default" profile.
        # See schroot.conf(5) and schroot-script-config(5) for further details.
        # The files detailed below may also be edited to further customise
        # this profile.

        # Filesystems to mount inside the chroot.
            FSTAB="/etc/schroot/qualnet/fstab"

        # Files to copy from the host system into the chroot.
            COPYFILES="/etc/schroot/qualnet/copyfiles"

        # System NSS databases to copy into the chroot.
            NSSDATABASES="/etc/schroot/qualnet/nssdatabases"

    * Create file /etc/schroot/qualnet/fstab
        # fstab: static file system information for chroots.
        # Note that the mount point will be prefixed by the chroot path
        # (CHROOT_PATH)
        #
        # <file system> <mount point>   <type>  <options>   <dump>  <pass>
        /proc       /proc       none    rw,rbind        0       0
        /sys        /sys        none    rw,rbind        0       0
        /dev            /dev            none    rw,rbind        0       0
        /home/jtrindade/workspace       /home/cnm/jtrindade/workspace   none    rw,bind     0   0

    * Create file /etc/schroot/qualnet/copyfiles
        # Files to copy into the chroot from the host system.
        #
        # <source and destination>
        /etc/resolv.conf
        /etc/gshadow

    * Create file /etc/schroot/qualnet/nssdatabases
        # System databases to copy into the chroot from the host system.
        #
        # <database name>





Packages to be installed
------------------------

Complete list at [TODO](http://somewhere.todo)

    * ack-grep
    * acl
    * apache2
    * automake
    * cacti
    * fio
    * gcc
    * git
    * logcheck
    * make
    * mercurial
    * mosh
    * parted
    * screen
    * strace
    * sudo
    * tmux
    * vim
    * zsh
    * rsync


TODO
----

 * Only allow ssh key (no passwords)??
 * Finnish configuring cacti (talk to Artur)
