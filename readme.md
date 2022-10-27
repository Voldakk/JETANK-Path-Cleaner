# JETANK Path Cleaner


## Prerequisites
- [JETANK AI Kit](https://www.waveshare.com/jetank-ai-kit.htm)
- \>32 GB SD Card
- [JetBot SD Card Image](https://jetbot.org/master/software_setup/sd_card.html)

## Installation

### Setup JetBot

Flash the SD card according to the instructions at [JetBot - Software Setup (SD Card Image)](https://jetbot.org/master/software_setup/sd_card.html).

### Expand the file system
As the JetBot image has limited free space, you may want to expand the file system to fill the entirity of the SD card.

```
$ sudo fdisk /dev/mmcblk0

Command (m for help): p
```
<details>
  <summary>Output</summary>
  
  ```
...
Device          Start      End  Sectors  Size Type
/dev/mmcblk0p1  28672 51228671 51200000 24.4G Linux filesystem
/dev/mmcblk0p2   2048     2303      256  128K Linux filesystem
/dev/mmcblk0p3   4096     4991      896  448K Linux filesystem
/dev/mmcblk0p4   6144     7295     1152  576K Linux filesystem
/dev/mmcblk0p5   8192     8319      128   64K Linux filesystem
/dev/mmcblk0p6  10240    10623      384  192K Linux filesystem
/dev/mmcblk0p7  12288    13055      768  384K Linux filesystem
/dev/mmcblk0p8  14336    14463      128   64K Linux filesystem
/dev/mmcblk0p9  16384    17279      896  448K Linux filesystem
/dev/mmcblk0p10 18432    19327      896  448K Linux filesystem
/dev/mmcblk0p11 20480    22015     1536  768K Linux filesystem
/dev/mmcblk0p12 22528    22655      128   64K Linux filesystem
/dev/mmcblk0p13 24576    24959      384  192K Linux filesystem
/dev/mmcblk0p14 26624    26879      256  128K Linux filesystem
...
  ```
</details>

If the output of the `p` command is identical to the output above, you may proceed with the following commands:

```
Command (m for help): d
Partition number (1-14, default 14): 1

Command (m for help): n
Partition number (1,15-128, default 1): [Press enter]
First sector (34-123596766, default 28672): [Press enter]
Last sector, +sectors or +size{K,M,G,T,P} (28672-123596766, default 123596766): [Press enter]
Do you want to remove the signature? [Y]es/[N]o: N

Command (m for help): w 

$ sudo resize2fs /dev/mmcblk0p1
```

### Setup JETANK in the jetbot docker container
```
$ sudo git clone https://github.com/waveshare/JETANK.git
$ cd JETANK/
$ sudo chmod +x config.sh
$ sudo chmod +x install.sh
$ ./config.sh jetbot
reboot
```
In the jetbot docker container. Accessed via the Jupiter notebook terminal in a browser: \
Address: `IP:8888` \
Password: `jetbot`

```
$ cd JETANK/
$ ./install.sh
$ sudo chmod 666 /dev/ttyTHS1
```

### Install jetson-inference in the jetbot docker container
I found the easiest way to do this is [building the project from source](https://github.com/dusty-nv/jetson-inference/blob/master/docs/building-repo-2.md) in the notebook terminal.

### Clone the repo
```
$ git clone git@gitlab.com:eivaun.experis/jetank-path-cleaner.git
```

## Usage
Notebook

## Contrubutors
Eivind Vold Aunebakk