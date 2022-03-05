# FC3000
![Alt text](imgs/main.jpg)
  
## Introduction
Since there are many variants (with different screen panel), all of steps written in here may not work on your FC3000. It means your FC3000 may become bricked ! FC3000 specs are almost same as miyoo handheld. So, I spend some time on porting kernel, which obtained source from miyoo repo in my github. Most of resources that include toolchain and buildroot are same as miyoo ones. Therefore, some steps written in here may be same as miyoo. If it is not clear in here, you can refer to miyoo repo. Now, all of porting tasks are complete, which can boot into GMenu2X desktop and play some porting games and emulators from open source. It is time to share to all of you, enjoy !

|Component|Description                                    |
|---------|-----------------------------------------------|
|CPU      |M900 XCM2010GP40 (Allwinner F1C100S)           |
|RAM      |32MB                                           |
|Screen   |2.8" 320x240                                   |
|Slot     |SDCard                                         |
|Gamepad  |DPad, 4 Buttons, Start, Select, L1, R1 and MENU|
|Port     |MicroUSB                                       |
|Battery  |3.7V 1100mA, AAA x 3                           |
|Dimension|140mm x 68mm x 18mm                            |
|Weight   |110g                                           |
  
## How to build Linux OS for FC3000
### Prepare environment
-  Install Debian 9 (x64)
  
### Prepare microsd (include prebuilt games and emulators)
```console
$ cd
$ wget https://github.com/steward-fu/fc3000/releases/download/v1.0/fc3000_tft_od_jutleys_no_roms.img.7z
$ 7za x fc3000_tft_od_jutleys_no_roms.img.7z
$ sudo dd if=fc3000_tft_od_jutleys_no_roms.img of=/dev/sdX bs=1M
```
  
### Configure toolchain
```console
$ cd
$ wget https://github.com/steward-fu/miyoo/releases/download/v1.0/toolchain.7z
$ 7za x toolchain.7z
$ sudo mv miyoo /opt/
$ export PATH=$PATH:/opt/miyoo/bin
```
  
### Build Kernel
```console
$ cd
$ https://github.com/steward-fu/fc3000/releases/download/source/kernel.tar.gz
$ tar xvf kernel.tar.gz
$ cd kernel
$ ARCH=arm CROSS_COMPILE=arm-linux- make suniv_defconfig
$ ./run.sh fc3000
```
  
## How to flash v1/v2 stock system (TFT screen only, not IPS)
1. download https://github.com/steward-fu/fc3000/releases/download/v1.0/fc3000_v1_v2_flash.img.7z
2. extract fc3000_v1_v2_flash.img and then write into microsd (SanDisk 8GB)
3. remove FC3000 cartridge (130 FC FAMES)
4. insert your microsd into FC3000
5. put battery back and then power on
6. SELECT: flash v1 system, START: flash v2 system  
![Alt text](https://steward-fu.github.io/website/handheld/fc3000/v1v2_flash/4.jpg)
7. takes about 3 mins  
![Alt text](https://steward-fu.github.io/website/handheld/fc3000/v1v2_flash/6.jpg)
8. complete  
![Alt text](https://steward-fu.github.io/website/handheld/fc3000/v1v2_flash/8.jpg)
9. remove your microsd and put stock microsd back  
  
v1 stock system (user must use original v1 microsd to play game)  
![Alt text](https://steward-fu.github.io/website/handheld/fc3000/v1v2_flash/10.jpg)
  
v2 stock system (user must use original v2 microsd to play game)  
![Alt text](https://steward-fu.github.io/website/handheld/fc3000/v1v2_flash/11.jpg)
  
### Forum(司徒开源): https://whycan.com/forumlist.php
### Home: https://steward-fu.github.io/website/index.htm
