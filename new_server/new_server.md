Hardware
--------

    * CPU: 2 x Intel Xeon E5-2640V2, LGA 2011, 2.0GHz, 8C/16T
    * RAM: 8 x DDR3 REG16G-1600DDR3, 16GB, DDR3-1600, Registered ECC, memory
    * Raid Controller: Backup for LSI SAS2208 + Bracket
    * Server: Supermicro SuperServer 6027R-72RF
    * Network cards: 2 x Intel Corporation I350 Gigabit Network Connection (rev 01)
        - eth0 (left): 00:25:90:e1:45:62
        - eth1 (right): 00:25:90:e1:45:63
    * IPMI
        - Mac address: 00-25-90-ce-d6-f6
    * Disks:
        Disk IDs were discovered with the following command:
        'find /dev/disk/by-id/ -iname 'scsi-*' | grep -v -- -part | while read disk ; do echo $(readlink $disk | sed -e s:../../:: ) $(basename $disk); done'

        - 2x SAMSUNG SSD 840 PRO 256GB SATA III
            - ID="sda scsi-36003048013ed380014b1776d0eee033d"
            - ID=""
        - 4x WESTERN DIGITAL 3TB SATA III 64MB RED
            - ID=""
            - ID=""
            - ID=""
            - ID=""


lspci command:

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

dmidecode:

    check dmidecode.txt file


IPMI Remote management
----------------------

    * Point the browser to the IPMI interface IP

    * Use IPMIView
        - ftp://ftp.supermicro.com/utility/IPMIView/Linux/


RAID
----

By hardware:


    Option 1
    Drive Groups
        - Virtual Drive 0 - RAID 5 - 8.185TB - Set boot drive ??? (Nao é boot drive)
            - Slot:0, SATA, HDD
            - Slot:1, SATA, HDD
            - Slot:4, SATA, HDD
            - Slot:5, SATA, HDD

        - Virtual Drive 1 - RAID 0 - 237.486 GB TODO
            - Slot:3, SATA, SDD

        - Virtual Drive 2 - RAID 0 - 237.486 GB TODO
            - Slot:7, SATA, SDD

    Option 2
    Drive Groups
        - Virtual Drive 0 - RAID 5 - 8.185TB
            - Slot:0, SATA, HDD
            - Slot:1, SATA, HDD
            - Slot:4, SATA, HDD
            - Slot:5, SATA, HDD

        - Virtual Drive 1 - RAID 1 - 237.486 GB 
            - Slot:3, SATA, SDD
            - Slot:7, SATA, SDD

    Option 3
    Drive Groups
        - Virtual Drive 0 - RAID 5 - 8.185TB - Set boot drive ??? (Nao é boot drive)
            - Slot:0, SATA, HDD
            - Slot:1, SATA, HDD
            - Slot:4, SATA, HDD
            - Slot:5, SATA, HDD

        - Virtual Drive 1 - RAID 0 - 2x237.486 GB
            - Slot:3, SATA, SDD
            - Slot:7, SATA, SDD

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

    Disk partition
        - 

TODO
----

Mudar pass do Ipmi
Desligar IPMI na interface normal
3 IPS - um privado
