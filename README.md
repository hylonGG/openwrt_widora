### 敬告某些国内厂家
##### Widora发布的MT7688 WI-FI驱动因版权限制只能运行在NEO、BIT模组、集成BIT模组的产品上，在其他7688上运行属于侵权行为，侵权必究。

### Hello everybody
##### [Twitter:widoraIoT](https://twitter.com/widora_io/)
##### TELEGRAM: https://t.me/widora
##### QQ Group: 299381903
##### https://widora.io   http://widora.cn

### ethmode command
| command |   status   |  
|---|---|
| ethmode l | only Port0,LAN |
| ethmode w | only Port0,WAN |
| ethmode wllll | Port0-Port4, Port0 is WAN,Port1-4 is LAN |
| ethmode lllll | Port0-Port4,all is LAN |


### wifimode command
| command |   status   |  
|---|---|
| wifimode ap | only AP,LAN |
| wifimode sta | only STA(apcli0),WAN |
| wifimode apsta | AP+STA,AP is LAN,STA is WAN |

### how to check if connected to some AP? use ap_client command,check return is ok or no
``` sh
$ ap_client
```
ok is connected
no is not connected

### How to compile?
# 1.install depend
## Ubuntu14.04
$ sudo apt-get update

$ sudo apt-get install git g++ make libncurses5-dev subversion libssl-dev gawk libxml-parser-perl unzip wget python xz-utils vim
## Macos
note: install brew and Xcode command line tools

$brew install coreutils findutils gawk gnu-getopt gnu-tar grep wget quilt xz

note: gnu-getopt is keg-only, so force linking it:brew ln gnu-getopt --force

# 2.download the source use git
$ git clone https://github.com/widora/openwrt_widora.git
# 3.update the feeds
$ cd openwrt_widora
$ ./scripts/feeds update -a

$ ./scripts/feeds install -a
# 4.config
$ make menuconfig
select the target:

Target System(Ralink RT288x/RT3xxx) --->

Subtarget(MT7688 based board) --->

Target Profile(Widora) --->

## note
Widora:16MB FLASH + 128MB RAM

Widora32M:32MB FLASH + 128MB RAM

# 5.make
$ make -j4
# 6.image
the binary image name like this in bin/ramips/:
openwrt-ramips-mt7688-Widora-squashfs-sysupgrade.bin
